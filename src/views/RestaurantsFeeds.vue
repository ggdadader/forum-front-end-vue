<template>
  <div class="container py-5">
     <NavTabs />
    <h1 class="mt-5">
      最新動態
    </h1>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <NewestRestaurants :restaurants="restaurants"/>
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments"/>
      </div>
    </div>
  </div>
</template>
<script>
import NavTabs from './../components/NavTabs'
import NewestRestaurants from './../components/NewestRestaurants'
import NewestComments from './../components/NewestComments'
const dummyData ={
  
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
        }
    ],
    "comments": [
        {
            "id": 1,
            "text": "Amet omnis molestiae qui asperiores est optio ducimus.",
            "UserId": 3,
            "RestaurantId": 1,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 5
            }
        },
        {
            "id": 2,
            "text": "Omnis recusandae qui.",
            "UserId": 3,
            "RestaurantId": 2,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 5
            }
        },
        {
            "id": 3,
            "text": "Est quis eum voluptatem aperiam rerum sed iusto.",
            "UserId": 3,
            "RestaurantId": 3,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 3
            }
        },
        {
            "id": 4,
            "text": "Excepturi nobis nesciunt aut est.",
            "UserId": 1,
            "RestaurantId": 4,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$rSLC7fxj6CaHKqyT8d.DEuxg.03y/usdkEPhiPg5WKuNsDa6l58im",
                "isAdmin": true,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 4
            }
        },
        {
            "id": 5,
            "text": "Dolores ratione exercitationem est perspiciatis fugiat.",
            "UserId": 3,
            "RestaurantId": 5,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 4
            }
        },
        {
            "id": 6,
            "text": "Dolorum ducimus hic rem maiores.",
            "UserId": 3,
            "RestaurantId": 6,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 2
            }
        },
        {
            "id": 7,
            "text": "Amet perspiciatis odio cum numquam deserunt dolor ducimus pariatur.",
            "UserId": 1,
            "RestaurantId": 7,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$rSLC7fxj6CaHKqyT8d.DEuxg.03y/usdkEPhiPg5WKuNsDa6l58im",
                "isAdmin": true,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 4
            }
        },
        {
            "id": 8,
            "text": "Natus velit qui sed.",
            "UserId": 3,
            "RestaurantId": 8,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 3
            }
        },
        {
            "id": 9,
            "text": "Dolor harum fugit est ut expedita velit.",
            "UserId": 3,
            "RestaurantId": 9,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 3,
                "name": "user2",
                "email": "user2@example.com",
                "password": "$2a$10$IrKZAVyS/oDuTXdcic1Sx.xvQVr77wv1qsXl.h/IYvhodIpKH7SH.",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 5
            }
        },
        {
            "id": 10,
            "text": "Aperiam expedita hic minus quas sint sed qui consequatur.",
            "UserId": 1,
            "RestaurantId": 10,
            "createdAt": "2021-11-13T22:34:02.000Z",
            "updatedAt": "2021-11-13T22:34:02.000Z",
            "User": {
                "id": 1,
                "name": "root",
                "email": "root@example.com",
                "password": "$2a$10$rSLC7fxj6CaHKqyT8d.DEuxg.03y/usdkEPhiPg5WKuNsDa6l58im",
                "isAdmin": true,
                "image": null,
                "createdAt": "2021-11-13T22:34:02.000Z",
                "updatedAt": "2021-11-13T22:34:02.000Z"
            },
            "Restaurant": {
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
                "CategoryId": 5
            }
        }
    ]
}

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data () {
    return {
      restaurants: [],
      comments: []
    }
  },
  created(){
    this.fetchFeeds()
  },
  methods:{
    fetchFeeds (){
      this.restaurants = dummyData.restaurants
      this.comments = dummyData.comments
    }
  }
}
</script>