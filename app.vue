<template>
  <section>
    <h1>キャラクター名</h1>
    <Nami/><!-- Nuxt.jsはオールインポート-->
    <MonkeyLuffy/><!-- サブフォルダも自動インポートでサブフォルダ名も含める-->
  </section>
</template>

<style>
section {
  border:limegreen 5px solid;
  margin:10px;
}
</style>