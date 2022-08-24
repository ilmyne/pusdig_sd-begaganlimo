this.order.products = this.product;
      axios
        .post("http://localhost:3000/Cart", this.order)
        .then(() => {
          this.$toast.success("Add to Cart!", {
            //nambahin atributnya si vue toast
            type: "success",
            position: "top-right",
            duration: 3000,
            dismissible: true,
          });
        })
        .catch((err) => console.log(err));
    },
  },

  deleteItem(id) {
      axios.delete("http://localhost:3000/cart/" + id).then(() => {
        this.$toast.error("Sukses Hapus Keranjang", {
          type: "error",
          position: "top-right",
          duration: 3000,
          dismissible: true,
        });
      });
      //   mengupdate
      axios
        .get("http://localhost:3000/cart")
        .then((response) => this.setCarts(response.data))
        .catch((error) => console.log(error));
    },

    <!-- totalan -->
                <tr>
                  <td colspan="5" aligh="right">
                    <bold>Total Price :</bold>
                  </td>
                  <td align="right">
                    <bold>Rp. {{ totalPrice }}</bold>
                  </td>
                </tr>

computed: {
      totalPrice() {
        return this.carts.reduce(function (items, data) {
          return items + data.products.harga * data.quantity;
        }, 0);
      },
    },