<template>
  <div>
    <template v-if="$auth.hasScope('teacher')">
      <div>
        <b-row>
          <b-col>
            <b-form-select v-model="selected1" :options="options1"/>
          </b-col>
        </b-row>
      </div>
    </template>
    <template v-if="$auth.hasScope('parent')">
      <div>
        <b-row>
          <b-col>
            <b-form-select v-model="selected2" :options="options2"/>
          </b-col>
        </b-row>
        <b-row>
          <hr />
        </b-row>
      </div>
    </template>
    <b-row>
      <b-col>
        <b-card title="Plan lekcji">
          <b-col>
            <template v-if="$auth.hasScope('teacher') && selected1=='a'">
              <div>
                <b-table bordered striped hover :items="items_1a" :fields="fields1">
                  <template v-slot:cell(spr1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr1"/>
                  </template>
                  <template v-slot:cell(spr2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr2"/>
                  </template>
                  <template v-slot:cell(spr3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr3"/>
                  </template>
                  <template v-slot:cell(odp1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp1"/>
                  </template>
                  <template v-slot:cell(odp2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp2"/>
                  </template>
                  <template v-slot:cell(odp3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp3"/>
                  </template>
                  <template v-slot:cell(proj1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.proj1"/>
                  </template>
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('teacher') && selected1=='b'">
              <div>
                <b-table bordered striped hover :items="items_1b" :fields="fields1">
                  <template v-slot:cell(spr1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr1"/>
                  </template>
                  <template v-slot:cell(spr2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr2"/>
                  </template>
                  <template v-slot:cell(spr3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr3"/>
                  </template>
                  <template v-slot:cell(odp1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp1"/>
                  </template>
                  <template v-slot:cell(odp2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp2"/>
                  </template>
                  <template v-slot:cell(odp3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp3"/>
                  </template>
                  <template v-slot:cell(proj1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.proj1"/>
                  </template>
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('teacher') && selected1=='c'">
              <div>
                <b-table bordered striped hover :items="items_1c" :fields="fields1">
                  <template v-slot:cell(spr1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr1"/>
                  </template>
                  <template v-slot:cell(spr2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr2"/>
                  </template>
                  <template v-slot:cell(spr3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.spr3"/>
                  </template>
                  <template v-slot:cell(odp1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp1"/>
                  </template>
                  <template v-slot:cell(odp2)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp2"/>
                  </template>
                  <template v-slot:cell(odp3)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.odp3"/>
                  </template>
                  <template v-slot:cell(proj1)="row">
                    <b-form-input type="text" size="sm" v-model="row.item.proj1"/>
                  </template>
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('teacher') && selected1==null">
              <div>
                <b>Wybierz klasę z menu powyżej!</b>
              </div>
            </template>
            <template v-if="$auth.hasScope('student')">
              <div>
                <b-table bordered striped hover :items="items2" :fields="fields2">
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('parent') && selected2=='a'">
              <div>
                <b-table bordered striped hover :items="items_3a" :fields="fields3">
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('parent') && selected2=='b'">
              <div>
                <b-table bordered striped hover :items="items_3b" :fields="fields3">
                </b-table>
              </div>
            </template>
            <template v-if="$auth.hasScope('parent') && selected2==null">
              <div>
                <b>Wybierz dziecko z menu powyżej!</b>
              </div>
            </template>
          </b-col>
        </b-card>
      </b-col>
    </b-row>
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
        selected1: null,
        options1: [
          {value: null, text: 'Wybierz klasę:'},
          {value: 'a', text: '4b'},
          {value: 'b', text: '5a'},
          {value: 'c', text: '6c'}
        ],

        selected2: null,
        options2: [
          {value: null, text: 'Wybierz dziecko:'},
          {value: 'a', text: 'Michał Kania'},
          {value: 'b', text: 'Elżbieta Kania'}
        ],

        fields1: ['Godz', 'poniedziałek', 'wtorek', 'Środa', 'czwartek', 'piątek'],
        items_1a: [
          {Godz: '8:15 - 9:00', poniedziałek: '', wtorek: ' ', Środa: 'Informatyka', czwartek: '', piątek: ''},
          {
            Godz: '9:10 - 9:55',
            poniedziałek: '',
            wtorek: '',
            Środa: 'Informatyka',
            czwartek: 'Fizyka',
            piątek: 'Chemia'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: '  J. polski',
            Środa: 'Matematyka',
            czwartek: 'Matematyka',
            piątek: 'Biologia'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'Geografia',
            wtorek: '  J. polski',
            Środa: 'Fizyka',
            czwartek: 'Matematyka',
            piątek: 'Biologia'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: '  J. angielski',
            Środa: 'Historia',
            czwartek: 'Fizyka',
            piątek: 'J. polski'
          },
          {
            Godz: '12:55 - 13:40',
            poniedziałek: 'Matematyka',
            wtorek: '  J. angielski',
            Środa: 'WF',
            czwartek: 'J. polski',
            piątek: 'J. polski'
          },
          {
            Godz: '13:50 - 14:35',
            poniedziałek: 'Fizyka',
            wtorek: '  Matematyka',
            Środa: '',
            czwartek: 'J. polski',
            piątek: 'J. angielski'
          },
          {Godz: '14:40 - 15:25', poniedziałek: 'Biologia', wtorek: '  WF', Środa: '', czwartek: '', piątek: ''},

        ],
        items_1b: [
          {
            Godz: '8:15 - 9:00',
            poniedziałek: 'Geografia',
            wtorek: '',
            Środa: 'Informatyka',
            czwartek: 'J. polski',
            piątek: ''
          },
          {
            Godz: '9:10 - 9:55',
            poniedziałek: 'Historia',
            wtorek: '',
            Środa: 'Informatyka',
            czwartek: 'Fizyka',
            piątek: 'Biologia'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: 'Informatyka',
            Środa: 'Matematyka',
            czwartek: 'Historia',
            piątek: 'Biologia'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'J. angielski',
            wtorek: ' Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Chemia'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: 'Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Fizyka'
          },
          {Godz: '12:55 - 13:40', poniedziałek: '', wtorek: '  J. polski', Środa: '', czwartek: 'Chemia', piątek: 'WF'},
          {Godz: '13:50 - 14:35', poniedziałek: '', wtorek: '  J. polski', Środa: '', czwartek: '', piątek: 'WF'},
          {Godz: '14:40 - 15:25', poniedziałek: '', wtorek: '', Środa: '', czwartek: '', piątek: ''},
        ],
        items_1c: [
          {Godz: '8:15 - 9:00', poniedziałek: 'Fizyka', wtorek: 'Historia ', Środa: '', czwartek: '', piątek: ''},
          {
            Godz: '9:10 - 9:55',
            poniedziałek: 'Biologia',
            wtorek: 'Matematyka',
            Środa: '',
            czwartek: 'Fizyka',
            piątek: 'Chemia'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: '  J. polski',
            Środa: 'Matematyka',
            czwartek: 'Matematyka',
            piątek: 'Biologia'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'Geografia',
            wtorek: '  J. polski',
            Środa: 'Chemia',
            czwartek: 'Matematyka',
            piątek: 'Biologia'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: '  J. angielski',
            Środa: 'Historia',
            czwartek: 'Fizyka',
            piątek: 'J. polski'
          },
          {
            Godz: '12:55 - 13:40',
            poniedziałek: 'Matematyka',
            wtorek: '  J. angielski',
            Środa: 'J. polski',
            czwartek: 'J. polski',
            piątek: 'WF'
          },
          {
            Godz: '13:50 - 14:35',
            poniedziałek: '',
            wtorek: '  ',
            Środa: 'Informatyka',
            czwartek: 'J. polski',
            piątek: 'WF'
          },
          {Godz: '14:40 - 15:25', poniedziałek: '', wtorek: ' ', Środa: 'Matematyka', czwartek: '', piątek: ''},
        ],

        fields2: ['Godz', 'poniedziałek', 'wtorek', 'Środa', 'czwartek', 'piątek'],
        items2: [
          {
            Godz: '8:15 - 9:00',
            poniedziałek: 'J. polski',
            wtorek: '',
            Środa: 'J. polski',
            czwartek: '',
            piątek: 'J. polski'
          },
          {
            Godz: '9:10 - 9:55',
            poniedziałek: 'Historia',
            wtorek: '',
            Środa: 'J. angielski',
            czwartek: 'Fizyka',
            piątek: 'Biologia'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: 'Informatyka',
            Środa: 'Matematyka',
            czwartek: 'Historia',
            piątek: 'Biologia'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'J. angielski',
            wtorek: ' Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Chemia'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: 'Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Fizyka'
          },
          {
            Godz: '12:55 - 13:40',
            poniedziałek: 'Geografia',
            wtorek: ' WF',
            Środa: 'Fizyka',
            czwartek: 'Chemia',
            piątek: ''
          },
          {Godz: '13:50 - 14:35', poniedziałek: '', wtorek: '  WF', Środa: '', czwartek: '', piątek: ''},
          {Godz: '14:40 - 15:25', poniedziałek: '', wtorek: '', Środa: '', czwartek: '', piątek: ''},
        ],


        fields3: ['Godz', 'poniedziałek', 'wtorek', 'Środa', 'czwartek', 'piątek'],
        items_3a: [
          {
            Godz: '8:15 - 9:00',
            poniedziałek: 'J. polski',
            wtorek: '  J. polski',
            Środa: '',
            czwartek: 'Historia',
            piątek: ''
          },
          {
            Godz: '9:10 - 9:55',
            poniedziałek: 'Historia',
            wtorek: '  Geografia',
            Środa: '',
            czwartek: 'Historia',
            piątek: 'Informatyka'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: '  Historia',
            Środa: 'Matematyka',
            czwartek: 'Matematyka',
            piątek: 'J. polski'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'Geografia',
            wtorek: '  Biologia',
            Środa: 'Matematyka',
            czwartek: 'Matematyka',
            piątek: 'J. polski'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: '  Biologia',
            Środa: 'Fizyka',
            czwartek: 'Fizyka',
            piątek: 'J. angielski'
          },
          {
            Godz: '12:55 - 13:40',
            poniedziałek: 'Matematyka',
            wtorek: '  Chemia',
            Środa: 'Chemia',
            czwartek: '',
            piątek: 'J. angielski'
          },
          {Godz: '13:50 - 14:35', poniedziałek: 'Fizyka', wtorek: '  ', Środa: 'WF', czwartek: '', piątek: ''},
          {Godz: '14:40 - 15:25', poniedziałek: '', wtorek: '  ', Środa: 'WF', czwartek: '', piątek: ''},
        ],
        items_3b: [
          {
            Godz: '8:15 - 9:00',
            poniedziałek: 'Geografia',
            wtorek: '',
            Środa: 'Informatyka',
            czwartek: 'J. polski',
            piątek: ''
          },
          {
            Godz: '9:10 - 9:55',
            poniedziałek: 'Historia',
            wtorek: '',
            Środa: 'Informatyka',
            czwartek: 'Fizyka',
            piątek: 'Biologia'
          },
          {
            Godz: '10:05 - 10:50',
            poniedziałek: 'Informatyka',
            wtorek: 'Informatyka',
            Środa: 'Matematyka',
            czwartek: 'Historia',
            piątek: 'Biologia'
          },
          {
            Godz: '11:05 - 11:50',
            poniedziałek: 'J. angielski',
            wtorek: ' Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Chemia'
          },
          {
            Godz: '12:00 - 12:45',
            poniedziałek: 'J. angielski',
            wtorek: 'Matematyka',
            Środa: 'Historia',
            czwartek: 'Matematyka',
            piątek: 'Fizyka'
          },
          {Godz: '12:55 - 13:40', poniedziałek: '', wtorek: '  J. polski', Środa: '', czwartek: 'Chemia', piątek: 'WF'},
          {Godz: '13:50 - 14:35', poniedziałek: '', wtorek: '  J. polski', Środa: '', czwartek: '', piątek: 'WF'},
          {Godz: '14:40 - 15:25', poniedziałek: '', wtorek: '', Środa: '', czwartek: '', piątek: ''},
        ]


      }
    }
  }
</script>
