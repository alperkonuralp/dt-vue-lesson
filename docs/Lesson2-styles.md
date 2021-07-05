# Styles for Lesson 2

## List.vue Styles

```scss
<style scoped lang="scss">
#list {
  button {
      font-size: 12pt;
      margin: 5px;
      padding: 5px 20px;
      width: 150px;
  }
}
</style>
```

## ListThumbnail.vue Styles

```scss
<style scoped lang="scss">
div.list.thumbnail {
  display: flex;
  // flex-direction: row;
  flex-wrap: wrap;
  align-items: flex-start;
  justify-content: space-between;
  // align-content: flex-start;
  background-color: #ddd;

  div.item {
    position: relative;
    border: 1px solid white;
    background-color: #bbb;
    width: 100px;
    height: 150px;
    padding: 5px;
    margin: 2px;
    transition: all 0.2s ease-in-out;
    cursor: pointer;
    overflow: hidden;

    img {
      width: 100px;
    }

    .code {
      text-align: center;
      font-weight: bold;
    }
    .title {
      text-align: center;
    }
    .region {
      text-align: center;
      font-style: italic;
    }

    &:hover {
      transform: scale(1.3);
      z-index: 1;
    }
  }
}
</style>
```

## ListTable.vue Styles

```scss
<style scoped lang="scss">
div.list.table {
  width: 800px;
  margin: 0 auto;
  background-color: #ddd;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;

  div.item {
    flex: 1 1 auto;
    width: 100%;
    display: flex;
    flex-direction: row;

    div {
      padding: 5px;
    }

    .image {
      flex: 1;
      align-self: center;

      img {
        width: 50px;
      }
    }
    .code {
      text-align: center;
      font-weight: bold;
      flex: 1;
      align-self: center;
    }
    .title {
      text-align: center;
      flex: 1;
      align-self: center;
    }
    .region {
      text-align: center;
      flex: 1;
      align-self: center;
    }
    .subregion {
      text-align: center;
      flex: 1;
      align-self: center;
    }

    &:hover{
      background-color: #bbb;
    }
  }

  .header {
    font-weight: bold;
    background-color: #ccc;
    padding: 10px 0;
  }
}
</style>
```