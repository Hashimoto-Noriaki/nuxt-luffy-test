<script setup lang="ts">
//型定義をインポートするときは import type
import type {Character} from "@/interfaces";
//キャラクターリストデータ。
useState<Map<number, Character>>(
  "characterList", //ステート名
  (): Map<number, Character> => { //初期値を生成
    const characterListInit = new Map<number, Character>();
    characterListInit.set(1, {id: 1, name: "ルフィ", bounty: 100000000});
    characterListInit.set(2, {id: 2, name: "ゾロ", bounty: 60000000});
    return characterListInit;
  }
);//characterListでデータの取り出しが可
</script>

<template>
  <BaseSection/>
</template>

<style>
section {
  border: blue 5px solid;
  margin: 10px;
}
</style>