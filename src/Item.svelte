<script>
  export let isActive = false;
  export let isFirst = false;
  export let isHover = false;
  export let getOptionLabel = undefined;
  export let item = undefined;
  export let filterText = '';

  let itemClasses = '';

  $: {
    const classes = [];
    if (isActive) { classes.push('active'); }
    if (isFirst) { classes.push('first'); }
    if (isHover) { classes.push('hover'); }
    if (item.isGroupHeader) { classes.push('groupHeader'); }
    if (item.isGroupItem) { classes.push('groupItem'); }
    itemClasses = classes.join(' ');
  }
</script>

<style>
  .item {
    cursor: default;
    height: 32px;
    height: var(--height, 42px);
    line-height: 32px;
    line-height: var(--height, 42px);
    padding: 0 20px;
    padding: var(--itemPadding, 0 20px);
    color: #5f5f5f;
    color: var(--itemColor, #000000);
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
  }

  .groupHeader {
    text-transform: uppercase;
    text-transform: var(--groupTitleTextTransform, uppercase);
    background-color: #e6e6e6;
  }

  .groupItem {
    padding-left: 20px;
    padding-left: var(--groupItemPaddingLeft, 40px);
    font-size: 1em;
    font-size: var(--groupItemFontSize, 12px);
  }

  .item:active {
    background: #b9daff;
    background: var(--itemActiveBackground, #b9daff);
  }

  .item.active {
    background:#007aff;
    background: var(--itemIsActiveBG, #007aff);
    color: #fff;
    color: var(--itemIsActiveColor, #fff);
  }

  .item.first {
    border-radius: 4px 4px 0 0;
    border-radius: var(--itemFirstBorderRadius, 4px 4px 0 0);
  }

  .item.hover:not(.active) {
    background: #e7f2ff;
    background: var(--itemHoverBG, #e7f2ff);
  }
</style>



<div class="item {itemClasses}">
  {@html getOptionLabel(item, filterText)}
</div>
