<template>
	<v-list dense>
		<v-list-group
			v-for="level1 in menus"
			:key="level1.id"
			:prepend-icon="level1.icono"
			no-action
		>
			<template v-slot:activator>
				<v-list-item-content>
					<v-list-item-title
          @click="cambiar()"
          v-text="level1.nombre"
          >
          </v-list-item-title>
				</v-list-item-content>
			</template>
			<v-list-item
				v-for="level2 in level1.submenu"
				:key="level2.id"
			>
				<v-list-item-content v-if="level2.submenu.length <= 0" style="cursor:pointer;" >
					<div class="ml-10">
						<v-list-item-title
							v-text="level2.nombre"
              @click="cambiar()"
						>
						</v-list-item-title>
					</div>
				</v-list-item-content>
				<v-list-item-content v-else >
					<div class="ml-10">
						<v-menu offset-x >
							<template v-slot:activator="{ on, attrs }">
								<v-list-item-title
									v-text="level2.nombre"
									v-bind="attrs"
									v-on="on"
									@click="level2.show = !level2.show"
								>
								</v-list-item-title>
							</template> 
							<v-list>
								<v-list-item
									v-for="(level3, index) in level2.submenu"
									:key="index"
									link
								>
									<v-list-item-title @click="cambiar();">
										{{ level3.nombre }}
									</v-list-item-title>
								</v-list-item>
							</v-list>
						</v-menu>
					</div>
				</v-list-item-content>
					<div v-if="level2.submenu.length > 0">
						<v-icon  v-show="!level2.show">mdi-menu-down</v-icon>
						<v-icon  v-show="level2.show">mdi-menu-right</v-icon>
					</div>
			</v-list-item>
		</v-list-group>
	</v-list>
</template>

<script  lang="ts">
import Vue from 'vue'

export default Vue.extend({
	name: 'Menu',

	methods: {
    cambiar() {
      this.menus.forEach(function(menu){
        menu.submenu.forEach(submenu => {submenu.show = false})
      });
    }
  },

	data: () =>  ({
		menus: 
      [
        {
          "id": 1,
          "menu_id": 0,
          "nombre": "Consultar Guia",
          "url": "#",
          "orden": 1,
          "icono": "mdi-magnify",
          "created_at": null,
          "updated_at": "2020-05-27T11:48:28.000000Z",
          "submenu": [],
        },
        {
          "id": 2,
          "menu_id": 0,
          "nombre": "Operaciones",
          "url": "#",
          "orden": 2,
          "icono": "mdi-cart",
          "created_at": null,
          "updated_at": "2020-05-27T11:48:28.000000Z",
          "submenu": [
            {
              "id": 1,
              "menu_id": 2,
              "nombre": "Procesamiento",
              "url": "#",
              "orden": 1,
              "icono": "mdi-run",
              "show": false,
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": [
                {
                  "id": 1,
                  "menu_id": 1,
                  "nombre": "tercero",
                  "url": "#",
                  "orden": 1,
                  "icono": "mdi-run",
                  "created_at": null,
                  "updated_at": "2020-05-27T11:48:28.000000Z",
                }
              ]
            },
            {
              "id": 2,
              "menu_id": 2,
              "nombre": "Fletes",
              "url": "#",
              "orden": 1,
              "icono": "mdi-bus-double-decker",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
            {
              "id": 3,
              "menu_id": 2,
              "nombre": "Recolectas",
              "url": "#",
              "orden": 1,
              "icono": "mdi-close-box",
              "show": false,
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": [{
                  "id": 1,
                  "menu_id": 1,
                  "nombre": "tercer nivel",
                  "url": "#",
                  "orden": 1,
                  "icono": "mdi-run",
                  "created_at": null,
                  "updated_at": "2020-05-27T11:48:28.000000Z",
                }]
            },
            {
              "id": 4,
              "menu_id": 2,
              "nombre": "Reportes",
              "url": "#",
              "orden": 1,
              "icono": "mdi-chart-bar",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
          ],
        },
        {
          "id": 3,
          "menu_id": 0,
          "nombre": "Administración",
          "url": "#",
          "orden": 3,
          "icono": "mdi-home",
          "created_at": null,
          "updated_at": "2020-05-27T11:48:28.000000Z",
          "submenu": [
            {
              "id": 1,
              "menu_id": 3,
              "nombre": "Caja Chica",
              "url": "#",
              "orden": 1,
              "icono": "mdi-cash-register",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
            {
              "id": 2,
              "menu_id": 3,
              "nombre": "Facturación",
              "url": "#",
              "orden": 1,
              "icono": "mdi-point-of-sale",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
            {
              "id": 3,
              "menu_id": 3,
              "nombre": "Cobranzas",
              "url": "#",
              "orden": 1,
              "icono": "mdi-receipt",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
            {
              "id": 4,
              "menu_id": 3,
              "nombre": "Reportes",
              "url": "#",
              "orden": 1,
              "icono": "mdi-chart-bar",
              "created_at": null,
              "updated_at": "2020-05-27T11:48:28.000000Z",
              "submenu": []
            },
          ],
        },
      ],
	})
})
</script>