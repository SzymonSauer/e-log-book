<template>
  <div>
<!--    <b-alert show variant="warning">This is a secure page!</b-alert>-->
	<template v-if="$auth.hasScope('teacher')">
		<div>
			<b-row>
				<b-col md="2">
					<b-form-select v-model="selected1" :options="options1"/>
				</b-col>
			</b-row>
		</div>
	</template>
	<template v-if="$auth.hasScope('parent')">
		<div>
			<b-row>
				<b-col md="2">
					<b-form-select v-model="selected2" :options="options2"/>
				</b-col>
			</b-row>
		</div>
	</template>
	<b-row>
      <b-col >
        <b-card title="Oceny">
		  <b-col md="5">
			<template v-if="$auth.hasScope('teacher') && selected1=='a'">
				<div >
					<b-table bordered striped hover :items="items_1a" :fields="fields1">
						<template  v-slot:cell(sprawdzian1)="row">
							<b-form-select size="sm" type="text" :options="opt" v-model="row.item.sprawdzian1"/>
						</template>
						<template v-slot:cell(sprawdzian2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian2"/>
						</template>
						<template v-slot:cell(sprawdzian3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian3"/>
						</template>
						<template v-slot:cell(odpowiedź1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź1"/>
						</template>
						<template v-slot:cell(odpowiedź2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź2"/>
						</template>
						<template v-slot:cell(odpowiedź3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź3"/>
						</template>
						<template v-slot:cell(projekt1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.projekt1"/>
						</template>
					</b-table>
				</div>
				<div>
					<b-button @click="showMsgBoxTwo">Zatwierdź</b-button>
				</div>
			</template>
			<template v-if="$auth.hasScope('teacher') && selected1=='b'">
				<div >
					<b-table bordered striped hover :items="items_1b" :fields="fields1">
						<template v-slot:cell(sprawdzian1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian1"/>
						</template>
						<template v-slot:cell(sprawdzian2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian2"/>
						</template>
						<template v-slot:cell(sprawdzian3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian3"/>
						</template>
						<template v-slot:cell(odpowiedź1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź1"/>
						</template>
						<template v-slot:cell(odpowiedź2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź2"/>
						</template>
						<template v-slot:cell(odpowiedź3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź3"/>
						</template>
						<template v-slot:cell(projekt1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.projekt1"/>
						</template>
					</b-table>
				</div>
				<div>
					<b-button @click="showMsgBoxTwo">Zatwierdź</b-button>
				</div>
			</template>
			<template v-if="$auth.hasScope('teacher') && selected1=='c'">
				<div >
					<b-table bordered striped hover :items="items_1c" :fields="fields1">
						<template v-slot:cell(sprawdzian1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian1"/>
						</template>
						<template v-slot:cell(sprawdzian2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian2"/>
						</template>
						<template v-slot:cell(sprawdzian3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.sprawdzian3"/>
						</template>
						<template v-slot:cell(odpowiedź1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź1"/>
						</template>
						<template v-slot:cell(odpowiedź2)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź2"/>
						</template>
						<template v-slot:cell(odpowiedź3)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.odpowiedź3"/>
						</template>
						<template v-slot:cell(projekt1)="row">
							<b-form-select type="text" size="sm" :options="opt" v-model="row.item.projekt1"/>
						</template>
					</b-table>
				</div>
				<div>
					<b-button @click="showMsgBoxTwo">Zatwierdź</b-button>
				</div>
			</template>
			<template v-if="$auth.hasScope('teacher') && selected1==null">
				<div >
					<b>Wybierz klasę z menu powyżej!</b>
				</div>
			</template>
			<template v-if="$auth.hasScope('student')">
				<div >
					<b-table bordered striped hover :items="items2" :fields="fields2">
					</b-table>
				</div>
			</template>
			<template v-if="$auth.hasScope('parent') && selected2=='a'">
				<div >
					<b-table bordered striped hover :items="items_3a" :fields="fields3">
					</b-table>
				</div>
			</template>
			<template v-if="$auth.hasScope('parent') && selected2=='b'">
				<div >
					<b-table bordered striped hover :items="items_3b" :fields="fields3">
					</b-table>
				</div>
			</template>
			<template v-if="$auth.hasScope('parent') && selected2==null">
				<div >
					<b>Wybierz dziecko z menu powyżej!</b>
				</div>
			</template>
		  </b-col>
        </b-card>
      </b-col>
<!--      <b-col md="4">-->
<!--        <b-card title="Scopes" class="mb-2">-->
<!--&lt;!&ndash;          Teacher: <b-badge>{{ $auth.hasScope('teacher') }}</b-badge>&ndash;&gt;-->
<!--&lt;!&ndash;          Student: <b-badge>{{ $auth.hasScope('student') }}</b-badge>&ndash;&gt;-->
<!--&lt;!&ndash;          Parent: <b-badge>{{ $auth.hasScope('parent') }}</b-badge>&ndash;&gt;-->
<!--        </b-card>-->
<!--        <b-card title="token">-->
<!--          {{ $auth.token || '-' }}-->
<!--        </b-card>-->
<!--      </b-col>-->
    </b-row>
    <hr>
    <b-btn-group>
<!--      <b-button @click="$auth.fetchUser()">Fetch User</b-button>-->
<!--      <b-button @click="$auth.logout()">Logout</b-button>-->
    </b-btn-group>
  </div>
</template>

<script>
    export default {
        middleware: ['auth'],
        computed: {
            state() {
                return JSON.stringify(this.$auth.$state, undefined, 2)
            }
        },
		data() {
			return {
				sel: null,
				opt: [
					{ value: null, text: '-' },
					{ value: 'a', text: '2' },
					{ value: 'b', text: '3' },
					{ value: 'c', text: '3.5' },
					{ value: 'd', text: '4' },
					{ value: 'e', text: '4.5' },
					{ value: 'f', text: '5' },
					{ value: 'g', text: 'nb' }
				],
			
				selected1: null,
				options1: [
					{ value: null, text: 'Wybierz klasę:' },
					{ value: 'a', text: '4b' },
					{ value: 'b', text: '5a' },
					{ value: 'c', text: '6c' }
				],

				selected2: null,
				options2: [
					{ value: null, text: 'Wybierz dziecko:' },
					{ value: 'a', text: 'Michał Kania' },
					{ value: 'b', text: 'Elżbieta Kania' }
				],

				fields1: ['imię', 'nazwisko', 'sprawdzian1', 'sprawdzian2', 'sprawdzian3', 'odpowiedź1', 'odpowiedź2', 'odpowiedź3', 'projekt1'],
				items_1a: [
					{ sprawdzian2: 3.5, odpowiedź2: .5, odpowiedź1: 4.5, sprawdzian1: 5, imię: 'Julia', nazwisko: 'Majewska' },
					{ sprawdzian2: 5, odpowiedź2: 4.5, odpowiedź1: 3.5, sprawdzian1: 4, imię: 'Zofia', nazwisko: 'Kowalska' },
					{ sprawdzian2: 'nb', odpowiedź1: 3.5, sprawdzian1: 'nb', imię: 'Szymon', nazwisko: 'Jóźwiak' },
					{ sprawdzian2: 'nb', odpowiedź2: 5, odpowiedź1: 4.5, odpowiedź2: 4, sprawdzian1: 'nb', imię: 'Maja', nazwisko: 'Karpińska' },
					{ sprawdzian2: 4, odpowiedź1: 5, sprawdzian1: 3.5, imię: 'Mikołaj', nazwisko: 'Grabowski' },
					{ sprawdzian2: 'nb', sprawdzian1: 5, imię: 'Lena', nazwisko: 'Wiśniewska' },
					{ sprawdzian2: 3.5, odpowiedź1: 3.5, sprawdzian1: 'nb', imię: 'Lena', nazwisko: 'Kowalczyk' },
					{ sprawdzian2: 4, sprawdzian1: 'nb', imię: 'Nina', nazwisko: 'Zalewska' },
					{ sprawdzian2: 4, odpowiedź2: 5, odpowiedź1: 5, sprawdzian1: 4.5, imię: 'Radosław', nazwisko: 'Markowski' },
					{ sprawdzian2: 5, odpowiedź1: 3.5, sprawdzian1: 4, imię: 'Jakub', nazwisko: 'Czech' }
				],
				items_1b: [
					{ sprawdzian2: 4.5, odpowiedź2: 4, odpowiedź1: 4, sprawdzian1: 5, imię: 'Michał', nazwisko: 'Bukowski' },
					{ sprawdzian2: 4, odpowiedź2: 4.5, odpowiedź1: 4, sprawdzian1: 3, imię: 'Jeremi', nazwisko: 'Sikorski' },
					{ sprawdzian2: 'nb', odpowiedź1: 3.5, sprawdzian1: 4, imię: 'Adam', nazwisko: 'Pawłowski' },
					{ sprawdzian2: 'nb', odpowiedź2: 5, odpowiedź1: 5, sprawdzian1: 'nb', imię: 'Jakub', nazwisko: 'Szewczyk' },
					{ sprawdzian2: 'nb', odpowiedź1: 4.5, sprawdzian1: 3.5, imię: 'Michał', nazwisko: 'Mucha' },
					{ sprawdzian2: 3.5, sprawdzian1: 4.5, imię: 'Natalia', nazwisko: 'Nowak' },
					{ sprawdzian2: 4.5, odpowiedź1: 5, sprawdzian1: 5, imię: 'Sylwia', nazwisko: 'Marciniak' },
					{ sprawdzian2: 5, sprawdzian1: 'nb', imię: 'Andrzej', nazwisko: 'Kubiak' }
				],
				items_1c: [
					{ sprawdzian2: 'nb', odpowiedź3: 4.5, odpowiedź2: 4, odpowiedź1: 4, sprawdzian1: 5, imię: 'Zuzanna', nazwisko: 'Jakubowska' },
					{ sprawdzian2: 4, odpowiedź2: 4.5, odpowiedź1: 4, sprawdzian1: 3, imię: 'Aleksandra', nazwisko: 'Jasińska' },
					{ sprawdzian2: 'nb', odpowiedź3: 4.5, odpowiedź1: 3.5, sprawdzian1: 4, imię: 'Mateusz', nazwisko: 'Sobczak' },
					{ sprawdzian2: 'nb', odpowiedź2: 45, odpowiedź1: 5, sprawdzian1: 'nb', imię: 'Mieszko', nazwisko: 'Szulc' },
					{ sprawdzian2: 'nb', odpowiedź2: 3.5, odpowiedź3: 4.5, odpowiedź1: 4.5, sprawdzian1: 3.5, imię: 'Magdalena', nazwisko: 'Błaszczyk' },
					{ sprawdzian2: 3.5, sprawdzian1: 'nb', imię: 'Kalina', nazwisko: 'Mikołajczyk' },
					{ sprawdzian2: 4.5, odpowiedź1: 5, sprawdzian1: 5, imię: 'Oliwia', nazwisko: 'Markowska' },
					{ sprawdzian2: 5, sprawdzian1: 5, imię: 'Zofia', nazwisko: 'Urbaniak' },
					{ sprawdzian2: 5, odpowiedź2: 4, odpowiedź1: 5, sprawdzian1: 4.5, imię: 'Blanka', nazwisko: 'Krawczyk' }
				],

				fields2: ['przedmiot', 'sprawdzian1', 'sprawdzian2', 'sprawdzian3', 'odpowiedź1', 'odpowiedź2', 'odpowiedź3', 'projekt1'],
				items2: [
					{ przedmiot: 'J. polski', sprawdzian1: 4, sprawdzian2: 3.5, odpowiedź1: 5 },
					{ przedmiot: 'Historia', sprawdzian1: 'nb', sprawdzian2: 5 },
					{ przedmiot: 'Informatyka', sprawdzian1: 3.5, sprawdzian2: 'nb', odpowiedź1: 4.5 },
					{ przedmiot: 'Geografia', odpowiedź1: 4 },
					{ przedmiot: 'J. angielski', sprawdzian1: 'nb', sprawdzian2: 5, odpowiedź1: 4.5, odpowiedź2: 4 },
					{ przedmiot: 'Matematyka', sprawdzian1: 5, sprawdzian2: 4, odpowiedź1: 4 },
					{ przedmiot: 'Fizyka', sprawdzian1: 3.5, sprawdzian2: 4, odpowiedź1: 5, odpowiedź2: 3.5, odpowiedź3: 4},
					{ przedmiot: 'Biologia', sprawdzian1: 'nb', odpowiedź1: 4.5 },
				],

				fields3: ['przedmiot', 'sprawdzian1', 'sprawdzian2', 'sprawdzian3', 'odpowiedź1', 'odpowiedź2', 'odpowiedź3', 'projekt1'],
				items_3a: [
					{ przedmiot: 'J. polski', sprawdzian1: 3.5, sprawdzian2: 4.5 },
					{ przedmiot: 'Historia', sprawdzian1: 'nb', sprawdzian2: 5, odpowiedź1: 3.5 },
					{ przedmiot: 'Informatyka', sprawdzian1: 'nb', sprawdzian2: 'nb', odpowiedź1: 4.5 },
					{ przedmiot: 'Geografia', sprawdzian1: 4, odpowiedź1: 4 },
					{ przedmiot: 'J. angielski', sprawdzian1: 3.5, sprawdzian2: 5, odpowiedź1: 4.5 },
					{ przedmiot: 'Matematyka', sprawdzian1: 5, sprawdzian2: 4, sprawdzian3: 4.5, odpowiedź1: 4 },
					{ przedmiot: 'Fizyka', sprawdzian1: 3.5, sprawdzian2: 4, odpowiedź1: 5, odpowiedź2: 3.5, odpowiedź3: 4},
					{ przedmiot: 'Biologia', sprawdzian1: 'nb', odpowiedź1: 4.5, odpowiedź2: 3.5 },
				],
				items_3b: [
					{ przedmiot: 'J. polski', sprawdzian1: 4.5, sprawdzian2: 3.5, odpowiedź1: 5, odpowiedź2: 4.5, odpowiedź3: 5 },
					{ przedmiot: 'Historia', sprawdzian1: 'nb', sprawdzian2: 4.5, odpowiedź1: 3.5 , odpowiedź2: 4},
					{ przedmiot: 'Informatyka', sprawdzian1: 4, sprawdzian2: 'nb', odpowiedź1: 4.5 },
					{ przedmiot: 'Geografia', sprawdzian1: 4, odpowiedź1: 4 },
					{ przedmiot: 'J. angielski', sprawdzian1: 'nb', sprawdzian2: 5, odpowiedź1: 4.5 },
					{ przedmiot: 'Matematyka', sprawdzian1: 5, sprawdzian2: 4, sprawdzian3: 4.5, odpowiedź1: 4 },
					{ przedmiot: 'Fizyka', sprawdzian1: 3.5, sprawdzian2: 4, sprawdzian3: 4, odpowiedź1: 5, odpowiedź2: 3.5, odpowiedź3: 4},
					{ przedmiot: 'Biologia', sprawdzian1: 'nb', odpowiedź1: 4.5, odpowiedź2: 3.5 },
				]
			}
		},
		methods: {
			showMsgBoxTwo() {
				this.boxTwo = ''
				this.$bvModal.msgBoxConfirm('Czy na pewno chcesz zatwierdzić oceny?', {
					title: 'Zatwierdź',
					okVariant: 'success',
					okTitle: 'TAK',
					cancelVariant: 'danger',
					cancelTitle: 'NIE',
					footerClass: 'p-2',
					hideHeaderClose: false,
					centered: true
				})
			}
		}
    }
</script>
