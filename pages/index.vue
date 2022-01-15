<template>
  <div>
    <div class="glide">
      <div class="glide__track" data-glide-el="track">
        <ul class="glide__slides">
          <li
            v-for="item in post.gallery"
            :key="item"
            class="glide__slide"
            style="background: black; display: flex; justify-content: center"
          >
            <img
              style="object-fit: contain; height: 400px"
              :src="imgUrl + item"
            />
          </li>
        </ul>
      </div>
      <div class="glide__arrows" data-glide-el="controls">
        <button class="glide__arrow glide__arrow--left" data-glide-dir="<">
          prev
        </button>
        <button class="glide__arrow glide__arrow--right" data-glide-dir=">">
          next
        </button>
      </div>
    </div>
    <section class="bg-white py-8">
      <div class="container mx-auto flex items-center flex-wrap pt-4 pb-12">
        <nav id="store" class="w-full z-30 top-0 px-6 py-1">
          <div
            class="w-full container mx-auto flex flex-wrap items-center justify-between mt-0 px-2 py-3"
          >
            <a
              class="uppercase tracking-wide no-underline hover:no-underline font-bold text-gray-800 text-xl"
              href="#"
            >
              {{ post.pageInfor.title }}
            </a>

            <div class="flex items-center" id="store-nav-content">
              <a
                class="pl-3 inline-block no-underline hover:text-black"
                href="#"
              >
                <svg
                  class="fill-current hover:text-black"
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path d="M7 11H17V13H7zM4 7H20V9H4zM10 15H14V17H10z" />
                </svg>
              </a>

              <a
                class="pl-3 inline-block no-underline hover:text-black"
                href="#"
              >
                <svg
                  class="fill-current hover:text-black"
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M10,18c1.846,0,3.543-0.635,4.897-1.688l4.396,4.396l1.414-1.414l-4.396-4.396C17.365,13.543,18,11.846,18,10 c0-4.411-3.589-8-8-8s-8,3.589-8,8S5.589,18,10,18z M10,4c3.309,0,6,2.691,6,6s-2.691,6-6,6s-6-2.691-6-6S6.691,4,10,4z"
                  />
                </svg>
              </a>
            </div>
          </div>
        </nav>

        <div class="block w-full overflow-x-auto mx-auto px-8">
          <table class="items-center bg-transparent w-full border-collapse">
            <thead>
              <tr>
                <th
                  class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
                >
                  Mức giá
                </th>
                <th
                  class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
                >
                  Diện tích
                </th>
                <th
                  class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
                >
                  Phòng ngủ - phòng tắm
                </th>
                <th
                  class="px-6 bg-blueGray-50 text-blueGray-500 align-middle border border-solid border-blueGray-100 py-3 text-xs uppercase border-l-0 border-r-0 whitespace-nowrap font-semibold text-left"
                >
                  Hướng
                </th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <th
                  class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4 text-left text-blueGray-700"
                >
                  {{ post.price }}
                </th>
                <td
                  class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                >
                  {{ post.acreage }}
                </td>
                <td
                  class="border-t-0 px-6 align-center border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                >
                  {{ post.roomStructure }}
                </td>
                <td
                  class="border-t-0 px-6 align-middle border-l-0 border-r-0 text-xs whitespace-nowrap p-4"
                >
                  {{ post.direction }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>

        <section class="w-full px-8">
          <h3 class="uppercase font-bold text-gray-800 text-xl pt-8" href="#">
            Thông tin mô tả
          </h3>
          <div v-html="post.description" class="pt-4 pb-8"></div>

          <h3 class="uppercase font-bold text-gray-800 text-xl pb-4">
            Nội thất
          </h3>
          <div v-for="furniture in post.furnitures" :key="furniture">
            <list-item :item-key="furniture" item-value="Có" />
          </div>

          <div v-if="project != null">
                <h3 class="uppercase font-bold text-gray-800 text-xl pt-8 pb-4">
                Tiện ích
                </h3>
                <div v-for="utility in project.utilities" :key="utility">
                  <list-item :item-key="utility" item-value="Có" />
                </div>

                <h3 class="uppercase font-bold text-gray-800 text-xl pt-8 pb-4">
                Đặc điểm bất động sản
                </h3>
                <list-item itemKey="Phòng" :itemValue="post.apartmentNumber"/>
                <list-item item-key="Tên dự án" :item-value="project.projectName" />
                <list-item item-key="Địa chỉ" :item-value="projectAddress" />
                <list-item item-key="Pháp lý" :item-value="project.juridical" />

                <h3 class="uppercase font-bold text-gray-800 text-xl pt-8 pb-4">
                  Xem trên bản đồ
                </h3>

                <iframe class="w-full mb-8" height="300" :src="project.address.googleMapLocation" loading="lazy"></iframe>
          </div>
        </section>
        <div
          v-for="item in post.gallery"
          :key="item"
          class="w-full md:w-1/3 xl:w-1/4 p-6 flex flex-col"
        >
          <a href="#">
            <img class="hover:grow hover:shadow-lg" :src="imgUrl + item" />
            <div class="pt-3 flex items-center justify-between">
              <p class="">{{ post.roomStructure }}</p>
              <svg
                class="h-6 w-6 fill-current text-gray-500 hover:text-black"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12,4.595c-1.104-1.006-2.512-1.558-3.996-1.558c-1.578,0-3.072,0.623-4.213,1.758c-2.353,2.363-2.352,6.059,0.002,8.412 l7.332,7.332c0.17,0.299,0.498,0.492,0.875,0.492c0.322,0,0.609-0.163,0.792-0.409l7.415-7.415 c2.354-2.354,2.354-6.049-0.002-8.416c-1.137-1.131-2.631-1.754-4.209-1.754C14.513,3.037,13.104,3.589,12,4.595z M18.791,6.205 c1.563,1.571,1.564,4.025,0.002,5.588L12,18.586l-6.793-6.793C3.645,10.23,3.646,7.776,5.205,6.209 c0.76-0.756,1.754-1.172,2.799-1.172s2.035,0.416,2.789,1.17l0.5,0.5c0.391,0.391,1.023,0.391,1.414,0l0.5-0.5 C14.719,4.698,17.281,4.702,18.791,6.205z"
                />
              </svg>
            </div>
            <p class="pt-1 text-gray-900">{{ post.price }}</p>
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import gql from "graphql-tag";
import ListItem from '../components/ListItem.vue';

export default {
  components: { ListItem },
  name: "IndexPage",
  data() {
    return {
      imgUrl: "https://maico-hub-record.ss-hn-1.bizflycloud.vn/",
    };
  },
  mounted() {
    new Glide(".glide", {
      type: "carousel",
      autoplay: 2000,
      hoverpause: true,
    }).mount();
  },
  apollo: {
    posts: gql`
      query GetPost {
        posts(
          where: {
            pageInfor: {
              slug: {
                eq: "can-ho-the-sun-avenue-3pn2wc-tang-17-thoai-mai-sang-trong-40072"
              }
            }
          }
        ) {
          id
          projectId
          gallery
          acreage
          price
          roomStructure
          direction
          description
          roomStructure
          furnitures
          apartmentNumber
          floor
          pageInfor {
            title
          }
        }
      }
    `,

    projects: { 
      query() {
          return gql`
            query GetProject($projectId: String!) {
                  projects(where: {id: {eq: $projectId}}) {
                  projectName
                  juridical
                  address {
                    street
                    district
                    city
                    googleMapLocation
                  }
                  utilities
              }
            }
          `;
      },

      skip() { return this?.posts == null; },

      variables() {
        return {
          projectId: this.post.projectId
        }
      },
    }
  },
  computed: {
    post() {
      return this.posts[0];
    },

    project() {
      return this.projects && this.projects[0];
    },

    projectAddress() {
      let address = this.project.address;
      return `${address.street}, ${address.district}, ${address.city}` 
    }
  },
};
</script>
