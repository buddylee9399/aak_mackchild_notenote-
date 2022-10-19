# THINGS IN HERE

## GEMS

```
gem "sassc-rails"
gem 'haml'
gem 'simple_form'
gem 'devise'
```
- sass rails for .scss files
- devise set for turbo, rails 7
- from: https://dev.to/efocoder/how-to-use-devise-with-turbo-in-rails-7-9n9
- haml for devise links

```
.header_inner
	= link_to image_tag( 'logo.svg'), root_path, id: "logo"
	%nav
		- if user_signed_in?
			= link_to "New Note", new_note_path
			= button_to "Sign Out", destroy_user_session_path, method: :delete
		- else
			= link_to "Log In", new_user_session_path

```

## MODELS
- devise user: has many notes
- notes belongs to user

## OTHER
- he did his own styling
- once authorized, user root path changes

```
Rails.application.routes.draw do
  devise_for :users
  get 'welcome/index'
  resources :notes

  authenticated :user do
    root "notes#index", as: "authenticated_root"
  end

  root "welcome#index"
end
```
