Link to deployed app:
https://nameless-brook-38351-5b786990f4d6.herokuapp.com

Files changed:
db/migrate/XXXXXX_add_done_to_todos.rb
app/models/todo.rb
app/controllers/todos_controller.rb
app/views/todos/_form.html.erb
app/views/todos/index.html.erb
config/routes.rb
Gemfile
Gemfile.lock

Migration:
class AddDoneToTodos < ActiveRecord::Migration[8.1]
  def change
    add_column :todos, :done, :boolean, default: false
  end
end

Controller change:
params.expect(todo: [:description, :done])

Form update:
<%= form.check_box :done %>
<%= form.label :done %>

Index display:
<p>Done: <%= todo.done ? "Yes" : "No" %></p>

Added routes:
get "/new_todo", to: "todos#new", as: "new_todo"
root "todos#index"

Added PostgreSQL gem (production only):
group :production do
  gem "pg", "~> 1.1"
end