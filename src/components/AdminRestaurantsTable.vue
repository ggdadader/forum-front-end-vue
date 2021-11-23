<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">
          #
        </th>
        <th scope="col">
          Category
        </th>
        <th scope="col">
          Name
        </th>
        <th
          scope="col"
          width="300"
        >
          操作
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="restaurant in restaurants"
        :key="restaurant.id"
      >
        <th scope="row">
          {{ restaurant.id }}
        </th>
        <td>{{ restaurant.Category ? restaurant.Category.name : '未分類' }}</td>
        <td>{{ restaurant.name }}</td>
        <td class="d-flex justify-content-between">
          <router-link
            :to="{name:'admin-restaurant', params:{id:restaurant.id}}"
            class="btn btn-link"
          >Show</router-link>

          <router-link
            :to="{name:'admin-restaurant-edit', params:{id:restaurant.id}}"
            class="btn btn-link"
          >Edit</router-link>

          <button
            type="button"
            class="btn btn-link"
            @click.prevent.stop="deleteRestaurant(restaurant.id)"
          >
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
const dummyData = {
    "restaurants": [
        {
            "id": 1,
            "name": "Flossie Lueilwitz",
            "tel": "1-952-957-1608",
            "address": "7201 Anahi Point",
            "opening_hours": "08:00",
            "description": "Et quibusdam excepturi ea. Laboriosam accusantium provident asperiores tempora sed rerum quia harum voluptas. Corrupti quo magnam qui animi consequuntur animi ipsum sit officia. Odit doloribus nihil. Velit at fugit aliquam officiis dolorem suscipit accusamus cupiditate. Et sit sed exercitationem quia facilis.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=23.021365402665616",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 2,
            "name": "Alvina Bergnaum",
            "tel": "423-255-7398 x33626",
            "address": "081 Eldora Land",
            "opening_hours": "08:00",
            "description": "vel qui eveniet",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=66.88861088535845",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 3,
            "name": "Miguel Smith",
            "tel": "838-114-9928 x669",
            "address": "42366 Vesta Alley",
            "opening_hours": "08:00",
            "description": "Vitae voluptatum asperiores nisi saepe et nihil eaque ipsa ullam. Corporis fugiat inventore enim voluptas iusto iste. Dolorem expedita nam sequi dolor est ex velit officia distinctio.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=55.14575048898658",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 4,
            "name": "Mose Harvey DDS",
            "tel": "407.323.0295 x53660",
            "address": "291 Schroeder Inlet",
            "opening_hours": "08:00",
            "description": "nulla",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=83.30362830349527",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 5,
            "name": "Cielo Monahan",
            "tel": "1-026-689-6180",
            "address": "1168 Roob Manors",
            "opening_hours": "08:00",
            "description": "Corrupti quibusdam et fugit reprehenderit iure minus quisquam. Quibusdam eligendi quisquam totam quisquam illo illo quia. Et odio voluptatibus labore.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=65.99277025563077",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 6,
            "name": "Carmen Strosin",
            "tel": "1-293-232-2219",
            "address": "395 Julie Vista",
            "opening_hours": "08:00",
            "description": "culpa",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=60.0491349299656",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 7,
            "name": "Scarlett Zieme",
            "tel": "209-999-2272 x093",
            "address": "2601 Fahey Ports",
            "opening_hours": "08:00",
            "description": "cupiditate",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=62.3077435762744",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 8,
            "name": "Alyson Leffler",
            "tel": "550.380.6446 x503",
            "address": "1916 Kunze Loaf",
            "opening_hours": "08:00",
            "description": "Sed in ut repellendus ipsum consequuntur iusto culpa aperiam. Delectus nostrum porro. Amet et ab non doloremque et. Et et quae tempore quis cumque. Qui adipisci officiis consequatur reprehenderit molestias nam id.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.41726613960335",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 9,
            "name": "Major Skiles III",
            "tel": "747.471.4885",
            "address": "00663 Wehner Club",
            "opening_hours": "08:00",
            "description": "Aperiam molestias sapiente voluptatem nam. Ut totam autem voluptas et reiciendis eum autem excepturi. Odit aperiam rerum incidunt iste et dolor laborum quod velit.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=66.1093392740336",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 10,
            "name": "Maverick Pacocha",
            "tel": "316-007-2152 x366",
            "address": "0236 Oren Keys",
            "opening_hours": "08:00",
            "description": "Odit alias sint et placeat optio hic eligendi nihil. Consequuntur aliquid magni. Quod pariatur ipsa aut occaecati rerum est. Qui alias alias nisi. Eos enim qui non incidunt maxime sint esse pariatur debitis.\n \rConsequatur in minima neque repellendus est ullam qui. Molestiae suscipit itaque asperiores recusandae libero. Deserunt qui porro omnis ut molestiae. Ullam aut aliquid dolorum voluptate facere consequatur sunt. Beatae sapiente mollitia quos eum dolor sed id.\n \rEt corporis non necessitatibus tempore. Suscipit animi inventore vitae recusandae vel explicabo quia veniam. Quaerat natus ipsam. Quidem quisquam consequuntur itaque dicta occaecati illum praesentium.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.982106075887934",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 11,
            "name": "Estevan Muller",
            "tel": "(361) 860-2406 x808",
            "address": "32248 Demetrius Unions",
            "opening_hours": "08:00",
            "description": "Quae saepe voluptas enim minus consequuntur commodi perferendis. Non error occaecati itaque. Fugiat placeat et autem sequi molestiae in sint doloremque. Sint quasi modi dignissimos enim suscipit eveniet dicta nesciunt. Autem aut enim officia consequatur nobis. Quia nam cupiditate velit.\n \rLabore similique quia et quos sint atque quo ut fuga. Sunt exercitationem aliquid. Voluptatem error sit labore beatae. Earum modi enim sed doloribus excepturi.\n \rItaque corporis consequuntur et est. Labore officiis sed et quia aut temporibus quod. Incidunt suscipit harum dolore et ab eum ipsam voluptas optio. Voluptatibus unde et consequuntur exercitationem quia accusantium et quis numquam. Alias consequatur eaque ut eum dolor odio aut. Amet amet nemo earum earum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=48.87940620517257",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 12,
            "name": "Ted Lind",
            "tel": "(015) 248-4333 x7873",
            "address": "127 Maxie Mountains",
            "opening_hours": "08:00",
            "description": "inventore",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.99972360427959",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 13,
            "name": "Melody Weber",
            "tel": "959.876.5801 x048",
            "address": "183 Wilkinson Burg",
            "opening_hours": "08:00",
            "description": "dignissimos",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=2.8068884511790015",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 14,
            "name": "Trace Steuber",
            "tel": "1-991-805-8141",
            "address": "9196 Gregoria Square",
            "opening_hours": "08:00",
            "description": "Qui assumenda odio.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=67.0929726133638",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 15,
            "name": "Edward Cartwright",
            "tel": "586-968-3913 x2254",
            "address": "77441 Sylvester Turnpike",
            "opening_hours": "08:00",
            "description": "Asperiores quos dolor sed doloremque consequatur vero itaque nihil. Recusandae non inventore soluta praesentium cupiditate aut. Voluptatum ad veritatis pariatur ut. Cupiditate nisi delectus. Distinctio optio id sed. Amet ullam quasi eveniet quisquam velit asperiores aspernatur.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.960120177074906",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 16,
            "name": "Emil Heaney",
            "tel": "1-967-166-9515 x359",
            "address": "9738 Clementine Orchard",
            "opening_hours": "08:00",
            "description": "Nostrum quas doloribus sunt vel. Quo praesentium illum quo sit cum doloremque fugiat soluta. Eveniet aspernatur magni pariatur quis eaque. Natus sunt rerum maxime dignissimos nihil et. Facilis tempore ipsam placeat. Accusamus totam voluptatibus quidem facere veniam quos ipsa qui aut.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.549762939458535",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 17,
            "name": "Ms. Zachary Gibson",
            "tel": "223.968.7204 x8647",
            "address": "97184 Richmond Parkway",
            "opening_hours": "08:00",
            "description": "Similique atque id.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=45.023843341139354",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 18,
            "name": "Vladimir Nader",
            "tel": "581-471-2546 x9633",
            "address": "52111 Blanda Crossing",
            "opening_hours": "08:00",
            "description": "Neque praesentium omnis alias. Dolore reprehenderit est atque blanditiis alias voluptas. Possimus voluptatem laboriosam quidem nostrum at eligendi eos. Ipsa blanditiis ut aut aut. Nesciunt placeat ut omnis placeat.\n \rMolestiae possimus vel dolorem sed sit dicta vel corrupti. Necessitatibus rerum velit quibusdam omnis numquam quia. Ut placeat qui quidem ut quaerat alias exercitationem provident architecto. Omnis fuga odit eligendi accusantium repudiandae provident quidem.\n \rIllo id recusandae id quod. Exercitationem delectus nesciunt repellendus cumque delectus vitae et. Placeat expedita corporis error est repellat. Molestias repellat exercitationem beatae minima nisi consequatur praesentium.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=35.74182732109896",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 19,
            "name": "Jordon Labadie",
            "tel": "(715) 642-6581 x78297",
            "address": "7475 Lysanne Summit",
            "opening_hours": "08:00",
            "description": "Est dolorem et temporibus aut neque excepturi. Laboriosam voluptas voluptates. Ut ut doloribus dolorem est possimus officia non. Aliquid temporibus unde et tenetur mollitia vitae commodi. Similique mollitia nihil nisi.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=80.08190340393007",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 20,
            "name": "Ricky Yundt",
            "tel": "091.295.0884",
            "address": "8736 Kilback Cove",
            "opening_hours": "08:00",
            "description": "Voluptas quia maiores. Voluptates ad nesciunt rerum. Non magni beatae culpa modi. Accusamus dolor animi ducimus quos minus quam dolorem nam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.561539398587529",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 21,
            "name": "Adriel Stokes",
            "tel": "1-360-584-7664",
            "address": "3673 Mckayla Turnpike",
            "opening_hours": "08:00",
            "description": "Facilis nihil ipsa est ad sint quo dolor consequuntur sit. Id fugiat et fugit qui vero et tenetur temporibus. Unde velit sunt voluptatem ducimus iure sapiente nihil recusandae. Voluptatem ut provident qui exercitationem et nemo provident.\n \rCupiditate sint aut voluptas nihil sint labore repellat. Dolores nostrum necessitatibus minus fugiat. Quas eos tempore voluptate et unde consequatur. Provident ut facilis. Dignissimos voluptates et perspiciatis magnam.\n \rDucimus nemo sed nam recusandae omnis dolorum. Rerum ut voluptas tempore aperiam ut nulla quia voluptatem. Facere laudantium dolores consectetur enim et. Delectus voluptatem nostrum repellat est sint provident et.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=74.4464032971005",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 22,
            "name": "Justice Brakus",
            "tel": "1-674-620-4336",
            "address": "56981 Nikolaus Keys",
            "opening_hours": "08:00",
            "description": "Cum aperiam repellendus. Aperiam amet est consequatur. Cumque et reiciendis rerum dolor enim. Voluptatem fugiat expedita quaerat eaque dolorem enim.\n \rFacere qui consequuntur atque perspiciatis nam sed. Consequuntur sit fugit voluptas. Et ut expedita itaque. Fugit corrupti voluptates quidem. Tempora nisi fugiat laudantium at. Quae minus ut exercitationem autem et aut corporis explicabo.\n \rSed iste ipsa similique doloribus voluptate occaecati sit aperiam dolores. Ut qui porro. Nesciunt et voluptas cum ab rem reiciendis repellendus. Neque facilis quae adipisci nobis ipsa sit. Et explicabo praesentium doloremque.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.04359125174999",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 23,
            "name": "Benny Ullrich",
            "tel": "393-239-7683 x814",
            "address": "674 Morar Divide",
            "opening_hours": "08:00",
            "description": "Totam voluptatem nihil. Eius hic dolore sed dignissimos qui quo magni. Nihil quae amet illo est consequatur. Necessitatibus non cupiditate rerum nobis vitae nemo.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.683693859876136",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 24,
            "name": "Louisa Halvorson",
            "tel": "(627) 835-4761 x6472",
            "address": "76376 Hodkiewicz Stream",
            "opening_hours": "08:00",
            "description": "tenetur ut rerum",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=56.76563863395856",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 25,
            "name": "Mr. Brett Lemke",
            "tel": "674-267-9535 x79846",
            "address": "4644 Shanahan Falls",
            "opening_hours": "08:00",
            "description": "Iusto consequatur est explicabo sed illo ab incidunt assumenda nisi.\nExcepturi hic sed assumenda voluptatem in qui nesciunt.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=10.936763202700694",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 26,
            "name": "Patrick Bashirian",
            "tel": "173-558-3728",
            "address": "39015 Christine Crossroad",
            "opening_hours": "08:00",
            "description": "Similique nostrum nam et deleniti voluptas ipsum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=6.275712294803282",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 27,
            "name": "Cornell Wuckert",
            "tel": "1-185-356-8399 x76347",
            "address": "03513 Vanessa Stream",
            "opening_hours": "08:00",
            "description": "Ad ea et iure ex aperiam labore quidem dolores sit.\nIpsa et accusamus officia rerum aperiam.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=1.0852141739669197",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 28,
            "name": "Verdie Frami",
            "tel": "379.019.1941",
            "address": "85894 Keely Village",
            "opening_hours": "08:00",
            "description": "Reprehenderit error laudantium. Tenetur cumque voluptatem animi consequatur optio officia et dolor excepturi. Magni hic in.\n \rQuis nam ea sed ut ad magni corporis hic. Nihil labore est consectetur ut odit doloremque ut necessitatibus accusantium. Quis deleniti id. Laudantium quia assumenda quo totam qui. Ducimus enim quis corrupti atque ad a. Velit quae dolore.\n \rDolores et doloribus tempora beatae similique debitis officiis. Quia nobis voluptatum quia praesentium et in doloribus accusantium. Consequatur corporis minus aut. Eos facilis sint consequatur et consequatur placeat cum. Cupiditate perferendis dolor doloribus animi itaque saepe.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=90.41789640713793",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 29,
            "name": "Birdie Bahringer",
            "tel": "009.279.3716",
            "address": "1017 Mohamed Neck",
            "opening_hours": "08:00",
            "description": "Nam et dicta et. Natus quam delectus autem hic iste. Sapiente animi aut. Eaque dolor nostrum in iure. Tempore ut ut dolores natus harum culpa aut exercitationem eos. Qui reprehenderit unde neque perspiciatis delectus laudantium.\n \rVoluptatem incidunt aut reiciendis. Nisi assumenda harum sapiente aut. Et explicabo maxime ipsa totam. Dolore consequuntur qui perspiciatis eius. Mollitia dignissimos rem.\n \rConsequuntur quae amet ipsam. Autem molestiae dicta consequatur iusto. Cumque error omnis corporis sit vel qui quo. Omnis nihil laudantium sed architecto eos molestiae et minus laborum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=23.398812007943448",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 30,
            "name": "Adelbert Crist",
            "tel": "629.624.5079 x513",
            "address": "11098 Weston Rest",
            "opening_hours": "08:00",
            "description": "Nostrum delectus est sed doloremque beatae quidem aut autem suscipit. Sapiente rerum deleniti labore deleniti impedit nesciunt velit. Ex facilis numquam qui consequatur ratione. Totam ullam accusamus sint quisquam optio qui consequatur error. Explicabo iusto laboriosam sit consectetur corporis consectetur laborum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.47425694703973",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 31,
            "name": "Anne Tromp",
            "tel": "1-117-886-5951",
            "address": "609 Cummerata Mountains",
            "opening_hours": "08:00",
            "description": "Facere dolorem soluta. Officiis dolor at fuga adipisci asperiores dolores placeat fugiat ad. Et impedit ex assumenda placeat facere. Delectus nobis deserunt. Quam laboriosam dolorem sunt esse ut iste est facilis ut.\n \rEst dolor et maiores laborum enim nihil. Et molestias vitae architecto. Optio iste inventore odio nostrum quas molestias ex. Quos natus non. Est quasi delectus repellendus autem consectetur consectetur cumque voluptatem.\n \rDolorem mollitia cumque autem voluptas rerum voluptatum enim mollitia placeat. Quis ullam mollitia quidem officia quae. Nostrum neque et enim dignissimos. Nihil quia ea voluptates enim aut tenetur.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.20550200043209",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 32,
            "name": "Augusta McGlynn",
            "tel": "1-046-297-8366 x97283",
            "address": "96426 Hand Mountains",
            "opening_hours": "08:00",
            "description": "vero reprehenderit perferendis",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=51.518702270498615",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 33,
            "name": "Janis Rodriguez",
            "tel": "(717) 043-7608 x880",
            "address": "5073 Satterfield Hill",
            "opening_hours": "08:00",
            "description": "Minima eum est similique et voluptas sapiente et ipsum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=75.20174394408991",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 34,
            "name": "Lue Schowalter",
            "tel": "302-873-1872 x68868",
            "address": "331 Conrad Bridge",
            "opening_hours": "08:00",
            "description": "Ipsam quos in qui porro sed id debitis.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=86.64880843596781",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 35,
            "name": "Armani Leffler",
            "tel": "575.312.8521",
            "address": "74730 Gleason Neck",
            "opening_hours": "08:00",
            "description": "Asperiores est inventore tempora velit. Soluta autem quia sint et molestiae incidunt voluptatem illum nam. Qui et ducimus nisi. Vel quisquam quam libero laboriosam quia est error. Eligendi quidem explicabo adipisci asperiores eos quibusdam inventore vitae. Beatae minus explicabo dolores asperiores asperiores.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.76680188143369",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 36,
            "name": "Rosemary Kilback",
            "tel": "435-137-5925",
            "address": "5553 Murazik Track",
            "opening_hours": "08:00",
            "description": "excepturi sed enim",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=99.61119376574314",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 37,
            "name": "Judge Mayer",
            "tel": "670.013.8729 x502",
            "address": "589 Mariane Plains",
            "opening_hours": "08:00",
            "description": "quis",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=53.69518638983608",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 38,
            "name": "Reta Kuhn",
            "tel": "(150) 813-8884 x614",
            "address": "4841 Agustina Estates",
            "opening_hours": "08:00",
            "description": "Voluptatem natus et veniam quos reprehenderit omnis et aut vel. Neque non earum. Voluptas aliquid repudiandae voluptatibus inventore eligendi laudantium minima quidem ullam. Reiciendis non iure sint. Aliquam dolores molestiae recusandae minima. Debitis sint et sit nesciunt maiores est.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=88.29353952403791",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 39,
            "name": "Kendra Hodkiewicz",
            "tel": "(989) 218-6409 x6156",
            "address": "30593 Kunde Mountain",
            "opening_hours": "08:00",
            "description": "Eligendi et magnam quasi eos explicabo quia. Sunt et eos beatae quibusdam qui nisi eos. Unde explicabo voluptate facilis maxime nihil nemo qui optio. Quasi quis quaerat voluptatem ducimus enim assumenda laudantium ex. Quam ad quae.\n \rSit porro enim. Officia voluptatem natus non voluptatum consectetur quia est dicta voluptas. Rerum fugiat quia cupiditate ut excepturi adipisci officiis nam. Deleniti a eum ab aliquid quas ullam facere. Dolorem est totam dolor rerum voluptate sint minima ipsa natus.\n \rQuidem nemo et quis dolores. Praesentium inventore at. Ipsum debitis natus autem consectetur. Eum non modi dicta minima ut qui et. Earum commodi in voluptatem omnis reiciendis. Voluptatem eum adipisci.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=48.52947981204605",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 40,
            "name": "Anthony Bailey",
            "tel": "753.917.7348 x22285",
            "address": "7011 Weber Terrace",
            "opening_hours": "08:00",
            "description": "Quo non sequi est. Libero dolorem quam consequatur ipsum. Autem iure quis eum quia maiores fuga rerum.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=27.505673883981487",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 41,
            "name": "Gladyce Yundt",
            "tel": "659-260-0750 x867",
            "address": "82081 Bryon Well",
            "opening_hours": "08:00",
            "description": "Rerum ducimus et.\nDelectus eos quia officiis ipsa est ea quibusdam.\nTempora dicta asperiores eum.\nPerspiciatis et cum cupiditate ipsum rerum.\nAliquam eum pariatur rerum praesentium quos molestiae dolor dignissimos.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.33184972914239",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 42,
            "name": "Hector Donnelly PhD",
            "tel": "676.853.0476 x597",
            "address": "77073 Nader Shores",
            "opening_hours": "08:00",
            "description": "Est iusto animi eos incidunt doloremque optio alias ea aut. Mollitia sequi nihil vel.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=73.4416417473136",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 43,
            "name": "Cole Gerhold",
            "tel": "106.246.2927",
            "address": "395 Sporer Field",
            "opening_hours": "08:00",
            "description": "ullam velit nesciunt",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=48.1709023276637",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 44,
            "name": "Dr. Vernice Stanton",
            "tel": "(988) 985-4625 x0128",
            "address": "6623 Kurt Cape",
            "opening_hours": "08:00",
            "description": "Inventore voluptatem porro est nemo laudantium nihil facere asperiores.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=27.53134764045648",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 45,
            "name": "Rashad McKenzie",
            "tel": "030-774-7461 x63957",
            "address": "759 Judge Run",
            "opening_hours": "08:00",
            "description": "Magnam non vel dignissimos ut cum ut officiis eos ut.\nQuod atque vel est consequatur.\nQuas molestiae impedit a.\nRem iusto laboriosam architecto.\nAdipisci consequatur repellendus reprehenderit esse.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=17.431614784562143",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 46,
            "name": "Jamie Anderson",
            "tel": "448.853.6355 x4613",
            "address": "360 Bruen Shoal",
            "opening_hours": "08:00",
            "description": "Voluptas in a dolorem autem eveniet mollitia expedita similique.\nEa error quod.\nFacilis mollitia corporis nesciunt totam sed est eaque.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=29.79983980978591",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 47,
            "name": "Angelina Hirthe",
            "tel": "(298) 131-1288 x40065",
            "address": "573 Kutch Terrace",
            "opening_hours": "08:00",
            "description": "Consequatur alias esse. Enim necessitatibus aliquam ex aspernatur eligendi enim dolore. Voluptatum qui sequi quo assumenda facilis ut.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.39765966271364",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 48,
            "name": "Mr. Vallie Huel",
            "tel": "558.507.1283 x9863",
            "address": "120 Torphy Gardens",
            "opening_hours": "08:00",
            "description": "Consequatur voluptatem non at libero incidunt qui consequatur quia saepe.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=31.818582844357145",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 2,
            "Category": {
                "id": 2,
                "name": "日本料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 49,
            "name": "Maverick Hegmann",
            "tel": "605-681-2384 x139",
            "address": "15690 Keshaun Motorway",
            "opening_hours": "08:00",
            "description": "Vitae autem totam ut repudiandae perferendis quam eligendi.\nEum rem quod consequatur aut quia rerum exercitationem.\nQuibusdam cum cumque.\nEst voluptate molestiae in porro dolores.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71365060812892",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        },
        {
            "id": 50,
            "name": "Jeffery Schinner IV",
            "tel": "262.066.7164 x6800",
            "address": "3442 Sigurd Lock",
            "opening_hours": "08:00",
            "description": "Eveniet sint accusantium.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.27823250052164",
            "viewCounts": 0,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            }
        }
    ]
}

export default {
  data () {
    return {
      restaurants: []
    }
  },
  created () {
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants () {
      this.restaurants = dummyData.restaurants
    },
    deleteRestaurant (restaurantId){
      this.restaurants = this.restaurants.filter(restaurant =>restaurant.id !== restaurantId)
    }
  }
}
</script>