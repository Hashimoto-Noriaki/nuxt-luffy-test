<script setup lang="ts">
//①子でPropsの準備
//親から受け取るプロパティはdefineProps()で型宣言する
//(1)Propsインターフェース(プロパティ・型)の定義
interface Props {
    name:string;
    bounty:number;
}

//(2)definePropsを実行し、Propsオブジェクトの設定
const props = defineProps<Props>();

//値を監視し、変更が検知される状態にする
const bounty = ref(props.bounty);

//[懸賞金アップ]ボタンをクリックした時のメソッド
const bountyUp = (): void => {
    bounty.value  += 1000;
}

</script>

<template>
    <section className="box">
        <p>{{ name }}</p>
        <p>懸賞金:{{bounty}}ベリー</p>
        <button v-on:click="bountyUp">懸賞金アップ</button>
    </section>
</template>

<style scoped>
.box {
    border:black 5px solid;
    padding:10px;
}

</style>