<style lang="postcss">
  .dashboard {
    padding-left: 20px;
    padding-top: 20px;
    padding-bottom: 20px;

    @media (--mobile) {
      padding: 20px 0px;
    }
  }
  .user-name {
    font-weight: bold;
  }
  .left-column {
    width: 614px;

    @media (--mobile) {
      width: 100%;
    }
  }
  .right-column {
    width: 330px;

    @media (--mobile) {
      width: 100%;
    }
  }
  .card-layout {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
  .summary-card,
  .member-card,
  .greeting {
    margin-bottom: 20px;
  }
  .greeting {
    @media (--mobile) {
      margin-left: 20px;
    }
  }
</style>

<script lang="ts">
  import SummaryCard from './SummaryCard.svelte';
  import MemberCard from './MemberCard.svelte';
  import {_} from 'svelte-i18n';
  import UsageDetailCard from './UsageDetailCard.svelte';
  import SpendingCard from './SpendingCard.svelte';

  const user = {
    name: 'Jay-flow',
    role: '대표 관리자',
    imageUrl: 'https://picsum.photos/50/50?random=1',
  };

  const community = {
    id: '1',
    name: 'dooboolab',
    currency: 'KRW',
    description: 'PREMIUM ACCOUNT',
    deposit: [
      {
        title: '이마트 강서마곡점',
        description: '쇼핑',
        price: 25000,
        currency: 'KRW',
        createdAt: '2020/02/01',
      },
      {
        title: '삼성화재 강남지점',
        description: '보험금',
        price: 1125000.0,
        currency: 'KRW',
        createdAt: '2020/02/01',
      },
      {
        title: '현대카드',
        description: '회식',
        price: -611000.0,
        currency: 'KRW',
        createdAt: '2020/02/01',
      },
      {
        title: '롯데수퍼 강일점',
        description: '쇼핑',
        price: 25000.0,
        currency: 'KRW',
        createdAt: '2020/02/01',
      },
      {
        title: '쿠팡',
        description: '부자재',
        price: 3000.0,
        currency: 'KRW',
        createdAt: '2020/02/01',
      },
    ],
  };

  const members = [
    {
      name: 'Hyochan',
      imageUrl: 'https://picsum.photos/50/50?random=1',
    },
    {
      name: 'Dean',
      imageUrl: 'https://picsum.photos/50/50?random=2',
    },
    {
      name: 'Herry',
      imageUrl: 'https://picsum.photos/50/50?random=3',
    },
    {
      name: 'Jay',
      imageUrl: 'https://picsum.photos/50/50?random=4',
    },
  ];
</script>

<div class="dashboard">
  <div class="sub-heading greeting">
    ✋️ {$_('Dashboard.hello')} <span class="user-name">{user.name}</span>
  </div>
  <div class="card-layout">
    <div class="left-column">
      <div class="summary-card">
        <SummaryCard community={community} user={user} />
      </div>
      <div>
        <UsageDetailCard deposits={community.deposit} />
      </div>
    </div>
    <div class="right-column">
      <div class="member-card">
        <MemberCard members={members} />
      </div>
      <div>
        <SpendingCard deposits={community.deposit} />
      </div>
    </div>
  </div>
</div>
