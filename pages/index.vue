<template>
  <div class="landing-page">
    <div class="px-0 sm:px-40">
      <section class="landing-hero pt-5">
        <div class="header__bg"></div>
        <div class="container mx-auto relative">
          <Navbar />
          <Hero />
        </div>
      </section>
      <Steps />
      <section class="container mx-auto pt-24">
        <div class="flex justify-between items-center">
          <div class="w-auto">
            <h2 class="text-3xl text-gray-900 mb-8">
              New projects you can <br />
              taken care of
            </h2>
          </div>
          <div class="w-auto mt-5">
            <NuxtLink class="text-gray-900 hover:underline text-md font-medium" to="/">
              View All
            </NuxtLink>
          </div>
        </div>
        <div class="flex mt-3 -mx-6">
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-1.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Robotic Hand
                </h4>
                <p class="text-md font-light text-gray-900">
                  Creating robotic hand for better movement
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 20%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>20%</div>
                  <div class="ml-auto font-semibold">Rp 100.000.000</div>
                </div>
              </div>
              <NuxtLink
                to="/projects/1"
                class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
              >
                Fund Now
              </NuxtLink>
            </div>
          </div>
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-2.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Auto Pilot Drone
                </h4>
                <p class="text-md font-light text-gray-900">
                  Self driving drone, no worry to drive again
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 45%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>45%</div>
                  <div class="ml-auto font-semibold">Rp 80.000.000</div>
                </div>
                <NuxtLink
                  to="/projects/2"
                  class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
                >
                  Fund Now
                </NuxtLink>
              </div>
            </div>
          </div>
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-3.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Wireboard
                </h4>
                <p class="text-md font-light text-gray-900">
                  The new era of mechanical keyboard
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 80%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>80%</div>
                  <div class="ml-auto font-semibold">Rp 40.000.000</div>
                </div>
                <NuxtLink
                  to="/projects/3"
                  class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
                >
                  Fund Now
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
        <div class="flex mt-3 -mx-6">
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-4.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Wireless Earphone
                </h4>
                <p class="text-md font-light text-gray-900">
                  Just pair to phone and ready to set
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 45%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>45%</div>
                  <div class="ml-auto font-semibold">Rp 55.000.000</div>
                </div>
                <NuxtLink
                  to="/projects/4"
                  class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
                >
                  Fund Now
                </NuxtLink>
              </div>
            </div>
          </div>
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-5.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Auto Heater
                </h4>
                <p class="text-md font-light text-gray-900">
                  Make the room keep warm automatically
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 70%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>70%</div>
                  <div class="ml-auto font-semibold">Rp 75.000.000</div>
                </div>
                <NuxtLink
                  to="/projects/5"
                  class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
                >
                  Fund Now
                </NuxtLink>
              </div>
            </div>
          </div>
          <div
            class="card-project w-1/3 mx-6 my-4 p-5 border border-gray-500 rounded-20"
          >
            <div class="item">
              <figure class="item-image">
                <img
                  src="/project-thumbnail-6.jpg"
                  alt=""
                  class="rounded-20 w-full"
                />
              </figure>
              <div class="item-meta">
                <h4 class="text-3xl font-medium text-gray-900 mt-5">
                  Smart Lock
                </h4>
                <p class="text-md font-light text-gray-900">
                  Open the door with just one tap and click
                </p>
                <div class="relative pt-4 progress-bar">
                  <div
                    class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
                  >
                    <div
                      style="width: 10%"
                      class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
                    ></div>
                  </div>
                </div>
                <div class="flex progress-info">
                  <div>10%</div>
                  <div class="ml-auto font-semibold">Rp 35.000.000</div>
                </div>
                <NuxtLink
                  to="/projects/6"
                  class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
                >
                  Fund Now
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
    <ClientTestimony />
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
export default {
  name: "IndexPage",
}
</script>
