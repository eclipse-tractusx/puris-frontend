<!--
 Copyright (c) 2022,2023 Volkswagen AG
 Copyright (c) 2022,2023 Fraunhofer-Gesellschaft zur Foerderung der angewandten Forschung e.V. (represented by Fraunhofer ISST)
 Copyright (c) 2022,2023 Contributors to the Eclipse Foundation
 
 See the NOTICE file(s) distributed with this work for additional
 information regarding copyright ownership.
 
 This program and the accompanying materials are made available under the
 terms of the Apache License, Version 2.0 which is available at
 https://www.apache.org/licenses/LICENSE-2.0.
 
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
 WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
 License for the specific language governing permissions and limitations
 under the License.
 
 SPDX-License-Identifier: Apache-2.0
-->

<script setup>
import { RouterLink, RouterView } from "vue-router";
const appName = import.meta.env.VITE_APP_NAME;
</script>

<template>
  <div class="flex">
    <div
        class="flex flex-col overflow-y-auto border-r w-64 fixed left-0 top-0 h-screen p-10"
    >
      <div>
        <h2 class="text-3xl font-semibold text-center text-blue-800">
          PURIS
        </h2>
      </div>
      <div class="flex flex-col justify-between mt-6">
        <aside>
          <ul class="space-y-2">
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/"
              ><img
                  class="mr-2"
                  src="@/assets/icons/home.svg"
                  alt="Icon"
              />Dashboard
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/createOrder"
              ><img
                  class="mr-2"
                  src="@/assets/icons/create.svg"
                  alt="Icon"
              />Create
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/stocks"
              ><img
                  class="mr-2"
                  src="@/assets/icons/stock.svg"
                  alt="Icon"
              />Stocks
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/manageOrders"
              ><img
                  class="mr-2"
                  src="@/assets/icons/manage.svg"
                  alt="Icon"
              />Manage
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/connectors"
              ><img
                  class="mr-2"
                  src="@/assets/icons/manage.svg"
                  alt="Icon"
              />Connectors
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/catalog"
              ><img
                  class="mr-2"
                  src="@/assets/icons/catalog.svg"
                  alt="Icon"
              />Catalog
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/negotiations"
              ><img
                  class="mr-2"
                  src="@/assets/icons/catalog.svg"
                  alt="Icon"
              />Negotiations
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/transfers"
              ><img
                  class="mr-2"
                  src="@/assets/icons/catalog.svg"
                  alt="Icon"
              />Transfers
              </RouterLink
              >
            </li>
            <li>
              <RouterLink
                  class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 dark:text-gray-100 dark:bg-gray-700 rounded-md"
                  to="/responses"
              ><img
                  class="mr-2"
                  src="@/assets/icons/responses.svg"
                  alt="Icon"
              />Responses
              </RouterLink
              >
            </li>
          </ul>
        </aside>
      </div>
    </div>
    <div class="sm:ml-64 lg:ml-0 content-center overflow-auto">
      <RouterView/>
    </div>
  </div>
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
  //display: grid; grid-template-columns: 1fr 1fr; padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
