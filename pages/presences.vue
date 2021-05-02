<template>
  <div>
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
      <b-col md="8">
        <b-card title="State">
		  <b-col md="5">
			<template v-if="$auth.hasScope('teacher') && selected1=='a'">
				<div >
					<b-table bordered striped hover :items="items_1a" :fields="fields1">
						<template v-slot:cell(obecność)="row">
							<b-form-checkbox size="sm" v-model="row.item.obecność" value="o" uncheck-value="nb" />
						</template>
						<template v-slot:cell(p1)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p1" />
						</template>
						<template v-slot:cell(p2)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p2" />
						</template>
						<template v-slot:cell(p3)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p3" />
						</template>
						<template v-slot:cell(p4)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p4" />
						</template>
						<template v-slot:cell(p5)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p5" />
						</template>
					</b-table>
				</div>
			</template>
			<template v-if="$auth.hasScope('teacher') && selected1=='b'">
				<div >
					<b-table bordered striped hover :items="items_1b" :fields="fields1">
						<template v-slot:cell(obecność)="row">
							<b-form-checkbox size="sm" v-model="row.item.obecność" value="o" uncheck-value="nb" />
						</template>
						<template v-slot:cell(p1)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p1" />
						</template>
						<template v-slot:cell(p2)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p2" />
						</template>
						<template v-slot:cell(p3)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p3" />
						</template>
						<template v-slot:cell(p4)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p4" />
						</template>
						<template v-slot:cell(p5)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p5" />
						</template>
					</b-table>
				</div>
			</template>
			<template v-if="$auth.hasScope('teacher') && selected1=='c'">
				<div >
					<b-table bordered striped hover :items="items_1c" :fields="fields1">
						<template v-slot:cell(obecność)="row">
							<b-form-checkbox size="sm" v-model="row.item.obecność" value="o" uncheck-value="nb" />
						</template>
						<template v-slot:cell(p1)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p1" />
						</template>
						<template v-slot:cell(p2)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p2" />
						</template>
						<template v-slot:cell(p3)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p3" />
						</template>
						<template v-slot:cell(p4)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p4" />
						</template>
						<template v-slot:cell(p5)="row">
							<b-form-input type="text" size="sm" v-model="row.item.p5" />
						</template>
					</b-table>
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
					<template v-slot:thead-top="data">
					<b-tr>
						<b-th colspan="1"><span class="sr-only">Name and ID</span></b-th>
						<b-th variant="primary" colspan="2">Poniedziałek 06.01</b-th>
						<b-th variant="primary" colspan="2">Wtorek 07.01</b-th>
						<b-th variant="primary" colspan="2">Środa 08.01</b-th>
						<b-th variant="primary" colspan="2">Czwartek 09.01</b-th>
						<b-th variant="primary" colspan="2">Piątek 10.01</b-th>
					</b-tr>
					</template>
					</b-table>
				</div>
			</template>
			
			<template v-if="$auth.hasScope('parent') && selected2=='a'">
				<div >
					<b-table bordered striped hover :items="items_3a" :fields="fields3">
										<template v-slot:thead-top="data">
					<b-tr>
						<b-th colspan="1"><span class="sr-only">Name and ID</span></b-th>
						<b-th variant="primary" colspan="2">Poniedziałek 06.01</b-th>
						<b-th variant="primary" colspan="2">Wtorek 07.01</b-th>
						<b-th variant="primary" colspan="2">Środa 08.01</b-th>
						<b-th variant="primary" colspan="2">Czwartek 09.01</b-th>
						<b-th variant="primary" colspan="2">Piątek 10.01</b-th>
					</b-tr>
					</template>
					</b-table>
				</div>
			</template>
			
			<template v-if="$auth.hasScope('parent') && selected2=='b'">
				<div >
					<b-table bordered striped hover :items="items_3b" :fields="fields3">
										<template v-slot:thead-top="data">
					<b-tr>
						<b-th colspan="1"><span class="sr-only">Name and ID</span></b-th>
						<b-th variant="primary" colspan="2">Poniedziałek 06.01</b-th>
						<b-th variant="primary" colspan="2">Wtorek 07.01</b-th>
						<b-th variant="primary" colspan="2">Środa 08.01</b-th>
						<b-th variant="primary" colspan="2">Czwartek 09.01</b-th>
						<b-th variant="primary" colspan="2">Piątek 10.01</b-th>
					</b-tr>
					</template>
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
      <b-col md="4">
        <b-card title="Scopes" class="mb-2">
          Teacher: <b-badge>{{ $auth.hasScope('teacher') }}</b-badge>
          Student: <b-badge>{{ $auth.hasScope('student') }}</b-badge>
          Parent: <b-badge>{{ $auth.hasScope('parent') }}</b-badge>
        </b-card>
        <b-card title="token">
          {{ $auth.token || '-' }}
        </b-card>
      </b-col>
    </b-row>
    <hr>
    <b-btn-group>
      <b-button @click="$auth.fetchUser()">Fetch User</b-button>
      <b-button @click="$auth.logout()">Logout</b-button>
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
    methods: {
      update() {

      }
    },
		data() {
			return {
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
					
        fields1: [{key:'obecność', label:'Dzisiejsza obecność'} , 'imię', 'nazwisko', { key: 'p1', label: '06.01' }, { key: 'p2', label: '07.01' }, { key: 'p3', label: '08.01' }, { key: 'p4', label: '09.01' }, { key: 'p5', label: '10.01' }],
				items_1a: [
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Julia', nazwisko: 'Majewska' },
					{ obecność: 'nb', p1: 'ob', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Zofia', nazwisko: 'Kowalska' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 's', p4: 's', p5: 's', imię: 'Szymon', nazwisko: 'Jóźwiak' },
					{ obecność: 'nb', p1: 'ob', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Maja', nazwisko: 'Karpińska' },
					{ obecność: 'nb', p1: 'ob', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Mikołaj', nazwisko: 'Grabowski' },
					{ obecność: 'nb', p1: 'ob', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Lena', nazwisko: 'Wiśniewska' },
					{ obecność: 'nb', p1: 'ob', p2: 's', p3: 'ob', p4: 's', p5: 'ob', imię: 'Lena', nazwisko: 'Kowalczyk' },
					{ obecność: 'nb', p1: 'ob', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Nina', nazwisko: 'Zalewska' },
					{ obecność: 'nb', p1: 'ob', p2: 's', p3: 'ob', p4: 'ob', p5: 'nb', imię: 'Radosław', nazwisko: 'Markowski' },
					{ obecność: 'nb', p1: 'nb', p2: 'nb', p3: 'nb', p4: 'nb', p5: 'nb', imię: 'Jakub', nazwisko: 'Czech' }
				],
				items_1b: [
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Michał', nazwisko: 'Bukowski' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Jeremi', nazwisko: 'Sikorski' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Adam', nazwisko: 'Pawłowski' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Jakub', nazwisko: 'Szewczyk' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Michał', nazwisko: 'Mucha' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Natalia', nazwisko: 'Nowak' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Sylwia', nazwisko: 'Marciniak' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Andrzej', nazwisko: 'Kubiak' }
				],
				items_1c: [
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Zuzanna', nazwisko: 'Jakubowska' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Aleksandra', nazwisko: 'Jasińska' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Mateusz', nazwisko: 'Sobczak' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Mieszko', nazwisko: 'Szulc' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Magdalena', nazwisko: 'Błaszczyk' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Kalina', nazwisko: 'Mikołajczyk' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Oliwia', nazwisko: 'Markowska' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Zofia', nazwisko: 'Urbaniak' },
					{ obecność: 'nb', p1: 's', p2: 'ob', p3: 'ob', p4: 'ob', p5: 'ob', imię: 'Blanka', nazwisko: 'Krawczyk' }
				],
				
        fields2: ['godzina', { key: 'pr1', label: 'Przedmiot' }, { key: 'p1', label: 'Obecność' }, { key: 'pr2', label: 'Przedmiot' },{ key: 'p2', label: 'Obecność' },{ key: 'pr3', label: 'Przedmiot' }, { key: 'p3', label: 'Obecność' },{ key: 'pr4', label: 'Przedmiot' }, { key: 'p4', label: 'Obecność' },{ key: 'pr5', label: 'Przedmiot' }, { key: 'p5', label: 'Obecność' }],
				items2: [
					{ godzina:'8.15-8.50', pr1: 'J.pol', p1: 'nb', pr2: 'Mat',		p2: 'ob', pr3: 'Bio',		p3: 'ob',	pr4: 'J.pol',		p4: 'ob', pr5: 'His',   p5: 'ob'},
					{ godzina:'9.10-9.45', pr1: 'His',   p1: 'nb', pr2: 'Bio',		p2: 'ob',	pr3: 'J.ang',	p3: 'ob',	pr4: 'Inf',		p4: 'ob', pr5: 'J.pol',  p5: 'ob'},
					{ godzina:'10.05-10.50', pr1: 'Inf',   p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Bio',  p5: 'ob'},
					{ godzina:'11.05-11.50', pr1: 'Geo',  p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Mat',  p5: 'ob'},
					{ godzina:'12.00-12.45', pr1: 'J.ang',p1: 'nb', pr2: 'His',	p2: 's',	pr3: 'Geo',		p3: 'ob', pr4: 'W-F',	p4: 'ob',	pr5: 'Inf',		p5: 'ob'},
					{ godzina:'12.55-13.40', pr1: 'Mat',  p1: 'nb', pr2: 'Fiz',		p2: 's',	pr3: 'J.pol',	p3: 'ob',	pr4: 'Geo',		p4: 'ob', pr5: 'J.ang',p5: 'ob'},
					{ godzina:'13.50-14.35', pr1: 'Fiz',  p1: 'nb', pr2: 'Geo',		p2: 's',	pr3: 'J.pol',	p3: 'ob', pr4: 'His',	p4: 'ob'},
					{ godzina:'14.40-15.25', pr2: 'W-F',	p2: 'nb', pr4: 'J.Mat',	p4: 'nb', pr3: 'His',   p3: 'nb'}
				],
				
				fields3: ['godzina', { key: 'pr1', label: 'Przedmiot' }, { key: 'p1', label: 'Obecność' }, { key: 'pr2', label: 'Przedmiot' },{ key: 'p2', label: 'Obecność' },{ key: 'pr3', label: 'Przedmiot' }, { key: 'p3', label: 'Obecność' },{ key: 'pr4', label: 'Przedmiot' }, { key: 'p4', label: 'Obecność' },{ key: 'pr5', label: 'Przedmiot' }, { key: 'p5', label: 'Obecność' }],
				items_3a: [
					{ godzina:'8.15-8.50', pr1: 'J.pol', p1: 'nb', pr2: 'Mat',		p2: 'ob', pr3: 'Bio',		p3: 'ob',	pr4: 'J.pol',		p4: 'ob', pr5: 'His',   p5: 'ob'},
					{ godzina:'9.10-9.45', pr1: 'His',   p1: 'nb', pr2: 'Bio',		p2: 'ob',	pr3: 'J.ang',	p3: 'ob',	pr4: 'Inf',		p4: 'ob', pr5: 'J.pol',  p5: 'ob'},
					{ godzina:'10.05-10.50', pr1: 'Inf',   p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Bio',  p5: 'ob'},
					{ godzina:'11.05-11.50', pr1: 'Geo',  p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Mat',  p5: 'ob'},
					{ godzina:'12.00-12.45', pr1: 'J.ang',p1: 'nb', pr2: 'His',	p2: 's',	pr3: 'Geo',		p3: 'ob', pr4: 'W-F',	p4: 'ob',	pr5: 'Inf',		p5: 'ob'},
					{ godzina:'12.55-13.40', pr1: 'Mat',  p1: 'nb', pr2: 'Fiz',		p2: 's',	pr3: 'J.pol',	p3: 'ob',	pr4: 'Geo',		p4: 'ob', pr5: 'J.ang',p5: 'ob'},
					{ godzina:'13.50-14.35', pr1: 'Fiz',  p1: 'nb', pr2: 'Geo',		p2: 's',	pr3: 'J.pol',	p3: 'ob', pr4: 'His',	p4: 'ob'},
					{ godzina:'14.40-15.25', pr2: 'W-F',	p2: 'nb', pr4: 'J.Mat',	p4: 'nb', pr3: 'His',   p3: 'nb'}
				],
				items_3b: [
					{ godzina:'8.15-8.50', pr1: 'J.pol', p1: 'nb', pr2: 'Mat',		p2: 'ob', pr3: 'Bio',		p3: 'ob',	pr4: 'J.pol',		p4: 'ob', pr5: 'His',   p5: 'ob'},
					{ godzina:'9.10-9.45', pr1: 'Fiz',  p1: 'nb', pr2: 'Geo',		p2: 's',	pr3: 'J.pol',	p3: 'ob', pr4: 'His',	p4: 'ob',	pr5: 'Inf',		p5: 'ob'},
					{ godzina:'10.05-10.50', pr1: 'Inf',   p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Bio',  p5: 'ob'},
					{ godzina:'11.05-11.50', pr1: 'Geo',  p1: 'nb', pr2: 'J.pol',	p2: 'ob',	pr3: 'Inf',		p3: 'ob', pr4: 'J.ang',	p4: 'ob', pr5: 'Mat',  p5: 'ob'},
					{ godzina:'12.00-12.45', pr1: 'J.ang',p1: 'nb', pr2: 'His',	p2: 's',	pr3: 'Geo',		p3: 'ob', pr4: 'W-F',	p4: 'ob',	pr5: 'Inf',		p5: 'ob'},
					{ godzina:'12.55-13.40', pr1: 'His',   p1: 'nb', pr2: 'Bio',		p2: 'ob',	pr3: 'J.ang',	p3: 'ob', pr4: 'J.Mat',	p4: 'nb', pr5: 'J.pol',  p5: 'ob'},
					{ godzina:'13.50-14.35', pr1: 'Fiz',  p1: 'nb', pr2: 'W-F',	p2: 'nb',	pr3: 'J.pol',	p3: 'ob', pr4: 'His',	p4: 'ob'},
					{ godzina:'14.40-15.25', pr3: 'His',   p3: 'nb'}
				]
			}
		}
    }
</script>
