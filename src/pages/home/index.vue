<template>
  <view class="page">
    <view class="date_container">
      <view class="time">23:06</view>
      <view class="date">2023年11月30日 星期四</view>
      <view class="search_container">
        <u-search
          bgColor="#fff"
          clearabled
          shape="round"
          :value="keyword"
          placeholder="快速搜索"
          :showAction="false"
          searchIconColor="#00ced6"
          @search="searchHandle">
        </u-search>
      </view>
      <view class="add_btn">
        <Icon icon="icon-add-bold" :size="20" color="#00ced6"></Icon>
      </view>
    </view>

    <view class="todo_list">
      <u-swipe-action>
        <u-swipe-action-item
          v-for="item in todoList"
          :key="item.id"
          :options="options1">
          <view class="todo_item">
            <view class="todo_item_dot"></view>
            <view class="todo_item_content">
              <view class="todo_item_title">
                <text>{{ item.title }}</text>
              </view>
              <view class="todo_item_time">
                <text>{{ item.time }}</text>
              </view>
            </view>
          </view>
        </u-swipe-action-item>
      </u-swipe-action>
    </view>
  </view>
</template>

<script setup lang="ts">
interface TodoItem {
  id: number;
  title: string;
  time: string;
}
const keyword = ref<string>("");
const options1 = [
  {
    text: "删除",
    style: {
      backgroundColor: "#f56c6c",
    },
  },
];
const todoList = ref<TodoItem[]>([
  {
    id: 1,
    title: "完成小程序分享功能",
    time: "2022-01-01",
  },
  {
    id: 2,
    title: "完成小程序分享功能",
    time: "2022-01-01",
  },
  {
    id: 3,
    title: "完成小程序分享功能",
    time: "2022-01-01",
  },
  {
    id: 4,
    title: "完成小程序分享功能",
    time: "2022-01-01",
  },
]);

const searchHandle = (value: string) => {
  keyword.value = value;
};
/**
 * 小程序分享示例
 */
onShareAppMessage((res) => {
  return {
    title: "Fish's Toolbox",
    path: "/pages/home/index",
    imageUrl: "/static/images/share.png",
  };
});
</script>

<style lang="scss" scoped>
// .u-search__content__input--placeholder {
//   text-align: center;
// }
.date_container {
  padding: 64rpx 32rpx 32rpx 32rpx;
  background-image: url("https://www.zowlsat.com/usr/uploads/2023/11/707266024.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  .time {
    font-size: 96rpx;
    color: #fff;
    text-shadow: 0 0 3px #333;
  }
  .date {
    color: #fff;
    text-shadow: 0 0 3px #333;
  }
  .search_container {
    margin-top: 64rpx;
    .search {
      background-color: red;
    }
  }
  .add_btn {
    position: absolute;
    right: 0;
    top: 0;
    width: 70rpx;
    height: 70rpx;
    margin: 32rpx;
    background-color: #fff;
    border-radius: 16rpx;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.todo_list {
  .todo_item {
    padding: 32rpx;
    border-bottom: 1px dashed #eee;
    display: flex;
    align-items: center;
    gap: 16rpx;
    &_dot {
      width: 38rpx;
      height: 38rpx;
      border-radius: 50%;
      border: 1px solid $theme;
    }
    &_dot.success {
      background-color: $theme;
    }
    &_content {
    }
    &_title {
      font-size: 32rpx;
    }
    &_time {
      font-size: 28rpx;
      color: #797979;
    }
  }
}
</style>
