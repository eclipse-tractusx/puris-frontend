<template>
  <main class="flex flex-col">
    <h1 class="w-full text-center bold text-5xl mb-6 pb-6">
      View and Manage Stocks
    </h1>

    <div>
      <form
          @submit.prevent="addOrUpdateStock(this.changedStock)"
          class="w-max max-w-lg"
      >
        <div class="flex flex-row justify-start space-x-3">
          <div class="space-x-2">
            <input
                type="radio"
                v-model="this.changedStock.type"
                value="Material"
                @change="toggleMaterialOrProduct(changedStock)"
            />
            <label>Material</label>
          </div>

          <div class="space-x-2">
            <input
                type="radio"
                v-model="this.changedStock.type"
                value="Product"
                @change="toggleMaterialOrProduct(changedStock)"
            />
            <label>Product</label>
          </div>
        </div>

        <div>
          <label for="material">Material</label>
          <select
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="materialSelect"
              v-model="this.changedStock.materialId"
              :disabled="this.changedStock.type === 'Product'"
          >
            <option v-for="material in this.materials" :value="material.id">
              {{ material.id }} ({{ material.name }})
            </option>
          </select>
        </div>
        <div>
          <label for="product">Product</label>
          <select
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              id="productSelect"
              v-model="this.changedStock.productId"
              :disabled="this.changedStock.type === 'Material'"
          >
            <option v-for="product in this.products" :value="product.id">
              {{ product.id }} ({{ product.name }})
            </option>
          </select>
        </div>
        <div>
          <label for="Quantity">Quantity</label>
          <input
              class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              type="number"
              id="quantityInput"
              v-model="this.changedStock.quantity"
          />
        </div>

        <div class="text-center">
          <button
              class="btn-primary"
              id="stockBtn"
          >
            Add or Update
          </button>
        </div>
      </form>

      <!-- separator -->
      <div id="materialAndProductStockTables" class="flex flex-col space-y-2 max-w-max">
        <StockTableSFC
            title="Material Stocks"
            :stocks="this.materialStocks"
            :partnerRole="'supplier'"
        />
        <StockTableSFC
            title="Product Stocks"
            :stocks="this.productStocks"
            :partnerRole="'customer'"
        />
      </div>
    </div>
  </main>
</template>

<script>
import StockTableSFC from "@/views/stock/StockTableSFC.vue";

export default {
  name: "StockView",
  components: {StockTableSFC},

  data() {
    return {
      changedStock: {
        materialId: "",
        productId: "",
        type: "Material",
        quantity: "",
        unitOfMeasure: "",
      },
      site: {
        bpns: "BPNS12345678910ZZZ",
        name: "Wolfsburg Hauptwertk",
      },
      materials: [
        {
          id: "M4711",
          name: "Central Control Unit",
          unitOfMeasure: "Parts",
        },
        {
          id: "M4712",
          name: "Steering Wheel",
          unitOfMeasure: "Parts",
        },
        {
          id: "M4713",
          name: "Wheel",
          unitOfMeasure: "Parts",
        },
      ],
      products: [
        {
          id: "P4711",
          name: "VW Golf",
          unitOfMeasure: "Parts",
        },
      ],
      materialStocks: [
        {
          id: "M4711",
          name: "Central Control Unit",
          quantity: "50",
          unitOfMeasure: "Parts",
        },
        {
          id: "M4712",
          name: "Steering Wheel",
          quantity: "50",
          unitOfMeasure: "Parts",
        },
        {
          id: "M4713",
          name: "Wheel",
          quantity: "200",
          unitOfMeasure: "Parts",
        },
      ],
      productStocks: [],
    };
  },
  methods: {
    addOrUpdateStock(changedStock) {
      if (changedStock.type === "Material") {
        var existingMaterialStock = this.materialStocks.filter(
            (stock) => stock.id === changedStock.materialId
        );

        if (existingMaterialStock.length === 1) {
          var material = existingMaterialStock[0];
          material.quantity = changedStock.quantity;
        } else {
          var existingMaterial = this.materials.filter(
              (m) => m.materialId === changedStock.materialId
          )[0];
          var newStock = {
            id: changedStock.materialId,
            name: existingMaterial.name,
            quantity: changedStock.quantity,
            unitOfMeasure: existingMaterial.unitOfMeasure,
          };
          this.materialStocks.push(newStock);
        }
      } else if (changedStock.type === "Product") {
        var existingProductStock = this.productStocks.filter(
            (stock) => stock.id === changedStock.productId
        );

        if (existingProductStock.length === 1) {
          var product = existingProductStock[0];
          product.quantity = changedStock.quantity;
        } else {
          var existingProduct = this.products.filter(
              (p) => p.id === changedStock.productId
          )[0];
          newStock = {
            id: changedStock.productId,
            name: existingProduct.name,
            quantity: changedStock.quantity,
            unitOfMeasure: existingProduct.unitOfMeasure,
          };
          this.productStocks.push(newStock);
        }
      }
    },
    toggleMaterialOrProduct(changedStock) {
      if (changedStock.type === "Material") {
        changedStock.productId = "";
      } else if (changedStock.type === "Product") {
        changedStock.materialId = "";
      }
    },
  },
};
</script>

<style scoped></style>