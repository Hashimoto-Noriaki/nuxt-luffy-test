<script setup lang="ts">
//キャラクターリストデータ。
const characterListInit = new Map<number, Character>();
characterListInit.set(1, {id: 1, name: "ルフィ", bounty: 100000000});
characterListInit.set(2, {id: 2, name: "ゾロ", bounty: 60000000});
const characterList = ref(characterListInit);

//懸賞金の合計の算出プロパティ。
const totalBounty = computed(
  (): number => {
    let total = 0;
    for(const character of characterList.value.values()) {
      total += character.bounty;
    }
    return total;
  }
);

//Emitにより実行されるメソッド。
const onIncrementBounty = (id: number): void => {
  //オブジェクトを取得。
  const character = characterList.value.get(id);
  //オブジェクトが存在するなら…
  if(character != undefined) {
    //懸賞金をアップ。
    character.bounty += 1000;
  }
}

//キャラクターインターフェース。
interface Character {
  id: number;
  name: string;
  bounty: number;
}
</script>

<template>
  <section>
    <h1>キャラクターリスト</h1>
    <p>懸賞金の合計: {{totalBounty}}</p>
    <OneCharacter2
      v-for="[id, character] in characterList"
      v-bind:key="id"
      v-bind:id="id"
      v-bind:name="character.name"
      v-bind:bounty="character.bounty"
      v-on:incrementBounty="onIncrementBounty"/>
  </section>
</template>