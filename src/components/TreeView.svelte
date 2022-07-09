<script>
  import TreeNode from './TreeNode.svelte'
    export let root;
</script>

<div class="treeview">
  <TreeNode {...root} type="folder" />
</div>

<style>

.treeview {
  background: #eee;
  border-radius: 1rem;
  padding: 1rem;
  user-select: none;
  width: 20rem;
}

</style>
