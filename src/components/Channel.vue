<template>
  <div class="grid h-full">
    <!-- <div class="col-12 md:col-3">
      <div class="card p-fluid">
        <h5>Connect Accounts</h5>
        <div class="mx-2">
          <div
            class="flex gap-2 align-items-center hover:bg-blue-50 py-2 pl-3 border-round-xl text-gray-700 focus:border-1 focus:border-blue-200 cursor-pointer active:text-blue-600 active:font-bold"
          >
            <i class="pi pi-amazon my-1"></i
            ><span class="my-1">Amazon store</span>
          </div>
          <div
            class="flex gap-2 align-items-center hover:bg-blue-50 py-2 pl-3 border-round-xl text-gray-700 focus:border-1 focus:border-blue-200 cursor-pointer active:text-blue-600 active:font-bold"
          >
            <i class="pi pi-shopping-bag my-1"></i
            ><span class="my-1">Seller cloud</span>
          </div>
          <div
            class="flex gap-2 align-items-center hover:bg-blue-50 py-2 pl-3 border-round-xl text-gray-700 focus:border-1 focus:border-blue-200 cursor-pointer active:text-blue-600 active:font-bold"
          >
            <i class="pi pi-palette my-1"></i><span class="my-1">Shopify</span>
          </div>
          <div
            class="flex gap-2 align-items-center hover:bg-blue-50 py-2 pl-3 border-round-xl text-gray-700 focus:border-1 focus:border-blue-200 cursor-pointer active:text-blue-600 active:font-bold"
          >
            <i class="pi pi-paypal my-1"></i
            ><span class="my-1">Amazon store</span>
          </div>
        </div>
      </div>
    </div>
    <div class="col-6">
      <div class="card p-fluid m-auto flex flex-column align-items-center">
        <h5 class="text-center">Connect Amazon Account</h5>
        <img class="w-2 my-3" src="\images\img\amazon.png" alt="" />
        <Button
          label="Connect Amazon Account"
          class="p-button-info mr-2 my-2"
        />
      </div>
    </div> -->
    <div class="col-12">
      <div class="grid">
        <div class="col-12 md:col-3">
          <div
            class="card p-fluid p-0 m-auto flex flex-column justify-content-between align-items-center h-full"
          >
            <div class="flex gap-3 header p-4">
              <img class="w-2 my-2" src="\images\img\amazon.png" alt="" />

              <div class="mt-1">
                <h5 class="mb-1">Amazon Store</h5>
                <p class="font-medium text-sm">
                  <i class="pi pi-sync text-gray-700 mr-1 text-xs"></i>
                  <span class="text-gray-700">Last sync:</span> Two days ago.
                </p>
              </div>
            </div>
            <div class="body px-4 pb-4">
              <div class="flex align-items-center">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-text"
                />
              </div>
              <div class="flex align-items-center text-red-500">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-danger p-button-text"
                />
                <Button
                  icon="pi pi-exclamation-circle"
                  class="p-button-rounded p-button-danger p-button-text"
                />
              </div>
              <div class="flex align-items-center text-red-500">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-danger p-button-text"
                />
                <Button
                  icon="pi pi-exclamation-circle"
                  class="p-button-rounded p-button-danger p-button-text"
                />
              </div>
            </div>
            <div
              class="flex justify-content-end w-full px-4 py-3 bg-gray-50 border-round-bottom-xl"
            >
              <Button
                label="Connect"
                icon="pi pi-arrow-right mt-1"
                iconPos="right"
                class="p-button-info w-auto"
              ></Button>
            </div>
          </div>
        </div>
        <div class="col-12 md:col-3">
          <div
            class="card p-fluid p-0 m-auto flex flex-column justify-content-between align-items-center h-full"
          >
            <div class="flex gap-3 header p-4">
              <img class="w-2 my-2" src="\images\img\cloud.png" alt="" />

              <div class="mt-1">
                <h5 class="mb-1">Seller Cloud</h5>
                <p class="font-medium text-sm">
                  <i class="pi pi-sync text-gray-700 mr-1 text-xs"></i>
                  <span class="text-gray-700">Last sync:</span> Two days ago.
                </p>
              </div>
            </div>
            <div class="body px-4 pb-4">
              <div class="flex align-items-center">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-text"
                />
              </div>
              <div class="flex align-items-center text-red-500">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-danger p-button-text"
                />
                <Button
                  icon="pi pi-exclamation-circle"
                  class="p-button-rounded p-button-danger p-button-text"
                />
              </div>
              <div class="flex align-items-center text-red-500">
                <label class="mr-6" for=""
                  ><i class="pi pi-user mr-1"></i> User Name</label
                >
                <Button
                  icon="pi pi-cog pi-spin"
                  class="p-button-rounded p-button-danger p-button-text"
                />
                <Button
                  icon="pi pi-exclamation-circle"
                  class="p-button-rounded p-button-danger p-button-text"
                />
              </div>
            </div>
            <div
              class="flex justify-content-end w-full px-4 py-3 bg-gray-50 border-round-bottom-xl"
            >
              <Button
                label="Connect"
                icon="pi pi-arrow-right mt-1"
                iconPos="right"
                class="p-button-info w-auto"
              ></Button>
            </div>
          </div>
        </div>
        <div class="col-12 md:col-3">
          <div
            class="card p-fluid p-0 m-auto flex flex-column justify-content-between align-items-center h-full"
          >
            <div class="flex gap-3 header p-4">
              <img class="w-2 my-2" src="\images\img\shopify.png" alt="" />

              <div class="mt-1">
                <h5 class="mb-1">Shopify</h5>
                <p class="font-medium text-sm">
                  <i class="pi pi-sync text-gray-700 mr-1 text-xs"></i>
                  <span class="text-gray-700">Last sync:</span> Two days ago.
                </p>
              </div>
            </div>

            <div class="body"></div>
            <div
              class="flex justify-content-end w-full px-4 py-3 bg-gray-50 border-round-bottom-xl"
            >
              <Button
                label="Connect"
                icon="pi pi-arrow-right mt-1"
                iconPos="right"
                class="p-button-info w-auto"
              ></Button>
            </div>
          </div>
        </div>
        <div class="col-12 md:col-3">
          <div
            class="card p-fluid p-0 m-auto flex flex-column justify-content-between align-items-center h-full"
          >
            <div class="flex gap-3 header p-4">
              <img class="w-2 my-2" src="\images\img\myntra.png" alt="" />

              <div class="mt-1">
                <h5 class="mb-1">Myntra</h5>
                <p class="font-medium text-sm">
                  <i class="pi pi-sync text-gray-700 mr-1 text-xs"></i>
                  <span class="text-gray-700">Last sync:</span> Two days ago.
                </p>
              </div>
            </div>
            <div class="body"></div>
            <div
              class="flex justify-content-end w-full px-4 py-3 bg-gray-50 border-round-bottom-xl"
            >
              <Button
                label="Connect"
                icon="pi pi-arrow-right mt-1"
                iconPos="right"
                class="p-button-info w-auto"
              ></Button>
            </div>
          </div>
        </div>

        <!-- <div class="col-12 md:col-3">
          <div class="card p-fluid m-auto flex flex-column align-items-center">
            <h5 class="text-center">Connect Paytm</h5>
            <img class="w-3" src="\images\img\paytm.png" alt="" />
            <Button
              label="Connect Paytm Account"
              class="p-button-info mr-2 my-2"
            />
          </div>
        </div>
        <div class="col-12 md:col-3">
          <div class="card p-fluid m-auto flex flex-column align-items-center">
            <h5 class="text-center">Connect ebay</h5>
            <img class="w-3" src="\images\img\ebay.png" alt="" />
            <Button
              label="Connect ebay Account"
              class="p-button-info mr-2 my-2"
            />
          </div>
        </div>
        <div class="col-12 md:col-3">
          <div class="card p-fluid m-auto flex flex-column align-items-center">
            <h5 class="text-center">Connect Snapdeal</h5>
            <img class="w-2 mt-2 mb-3" src="\images\img\snapdeal.png" alt="" />
            <Button
              label="Connect Snapdeal Account"
              class="p-button-info mr-2 mb-2 mt-3"
            />
          </div>
        </div> -->
      </div>
    </div>
  </div>
</template>
<style scoped>
.bg-opacity-10 {
  --tw-bg-opacity: 0.1;
}
.background-linear {
  background-image: linear-gradient(180deg, white, rgba(255, 255, 255, 0));
}
</style>
