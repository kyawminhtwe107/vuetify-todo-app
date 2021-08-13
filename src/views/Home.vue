<template>
  	<div class="home">

		<v-text-field
			class="pa-3"
            outlined
			hide-details
            label="Add Task"
            append-icon="mdi-plus"
			clearable
			v-model="newTask"
			@click:append="addTask"
			@keyup.enter="addTask"
        ></v-text-field>
		
		<v-list
			subheader
			two-line
			flat
		>
			<v-subheader>My Daily Tasks</v-subheader>

			<v-list-item-group>
				<v-list-item 
					v-for="task in tasks" 
					:key="task.id"
					@click="doneTask(task.id)"
					:class="{'blue lighten-5': task.done}"
				>
					<template v-slot:default>
						<v-list-item-action>
							<v-checkbox
								:input-value="task.done"
								color="primary"
							></v-checkbox>
						</v-list-item-action>

						<v-list-item-content>
							<v-list-item-title
								:class="{'text-decoration-line-through': task.done}"
							>
								{{task.title}}
							</v-list-item-title>
						</v-list-item-content>
						<v-list-item-action>
							<v-btn 
								icon
								@click.stop="deleteTask(task.id)"
							>
								<v-icon color="red lighten-1">mdi-delete</v-icon>
							</v-btn>
						</v-list-item-action>
					</template>
				</v-list-item>

			</v-list-item-group>
		</v-list>
		
  	</div>
</template>

<script>

  	export default {
    	name: 'Home',

		data(){
			return{
				newTask:'',
				tasks:[
					
				]
			}
		},
		methods:{
			addTask(){
				let task = {
					id:this.tasks.length + 1,
					title:this.newTask,
					done:false
				}

				this.tasks.push(task)
				this.newTask = ''
			},
			doneTask(id) {
				let task = this.tasks.find(task => task.id === id)

				task.done = !task.done
			},
			deleteTask(id){
				this.tasks = this.tasks.filter(task => task.id !== id)
			}
		}
  	}
</script>
