## Gems
- gem "mongoid-paperclip", "~> 0.0.8", :require => "mongoid_paperclip"
- gem "aws-s3", :require => "aws/s3"
- bundle install


## Model
include Mongoid::Paperclip

#### Photos Model Method (Having multiple photos belong to another Model)
Include in Photo model
> belongs_to :your_model_that_photos_belong_to
> has_mongoid_attached_file :image
> validates_attachment_content_type :image, content_type: ["image/jpg", "image/jpeg", "image/png", "image/gif"]

#### Avatar Method (Adding one photo to existing model)
Include in your model
> has_mongoid_attached_file :image
> validates_attachment_content_type :image, content_type: ["image/jpg", "image/jpeg", "image/png", "image/gif"]


## Controller
- Add :image to the params of that controller to enable it to accept an uploaded file in the view


## View
> In your view for that model (wherever you would like the user to be able upload the image (index, show, new))

#### Photos Model Method (views)
New
> <%= form_for @photo, {url: photos_path(@photo)} do |f| %>
>    <%= f.file_field :image %>
>   <%= f.submit "Upload" %>
> <% end %>

#### Avatar Method (views)
New
> <%= form_for @your_model_name do |f| %>
>    <%= f.file_field :image %>
>   <%= f.submit "Upload" %>
> <% end %>
Show
> <%= image_tag @photo.image.url %>

Let me know if something is not working or you see something that needs to be changed!

