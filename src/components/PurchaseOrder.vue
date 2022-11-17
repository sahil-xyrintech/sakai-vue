<template>
  <div class="card">
    <h1 class="text-center">Purchase Order</h1>
    <div class="grid">
      <div class="col">
        <div class="grid">
          <div class="col">
            <input
              class="p-2 underline border-none focus:border-bottom"
              type="text"
              placeholder="Purchase Order No."
            />
          </div>
          <div class="col">
            <input class="border-x-none border-top-none p-2" type="text" />
          </div>
        </div>
        <div class="grid">
          <div class="col">
            <input
              class="p-2 underline border-none focus:border-bottom"
              placeholder="Purchase Order details"
              type="text"
            />
          </div>
          <div class="col">
            <input class="border-x-none border-top-none p-2" type="text" />
          </div>
        </div>
      </div>
      <div class="col flex justify-content-end">
        <div class=""><input type="file" /></div>
      </div>
    </div>
  </div>
</template>
