<script>
  import TreeView from './components/TreeView.svelte';

  const root = {
      name: 'Tree root',
      folders: [{
        name: 'alfa',
        folders: [{
          name: 'Foo',
          files: [{
            name: 'test.file'
          }]
        }],
        files: [{
          name: 'first file'
        }, {
          name: 'second file'
          }]
      }, {
        name: 'bravo'
      },
      {
        name: 'charlie',
        folders: [{
          name: 'Foo',
          files: [{
            name: 'test.file'
          }]
        }],
        files: [{
          name: 'first file'
        }, {
          name: 'second file'
          }]
      }]
  };

</script>

<main>
  <TreeView root={root}/>
</main>

<style>
  :root {
    font-family: 'Lexend Deca', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
</style>
