### Gems
- gem "mongoid-paperclip", "~> 0.0.8", :require => "mongoid_paperclip"
- gem "aws-s3", :require => "aws/s3"
- bundle install

### Model
-include Mongoid::Paperclip

#### Avatar Method (Adding one photo to existing model)
- Include in your model
> has_mongoid_attached_file :image
> validates_attachment_content_type :image, content_type: ["image/jpg", "image/jpeg", "image/png", "image/gif"]

#### Photos Controller Method (Having multiple photos belong to another Model)
-Include in your model
> belongs_to :your_model_that_photos_belong_to
> has_mongoid_attached_file :image
> validates_attachment_content_type :image, content_type: ["image/jpg", "image/jpeg", "image/png", "image/gif"]
