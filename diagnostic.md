# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
    Join tables are valuable for Many to Many relationship for two entites. A table
    is not available to present many to many relationship, therefore the join tables have to be create to connect the two entities.
  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
  The Main tables are Profiles and Movies, both of them have many favorites. The join table Favorites has two foreign keys, profile_id and movie_id. Also, one favorite belongs to one movie and one profile.
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
  has_many :favorites
  end
  ```

  ```rb
  class Movie < ActiveRecord::Base
  has_many :favorites
  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
  belongs_to :movie
  belongs_to :profile
  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
  Modify the attribute of Json response.
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
  attributes :id, :given_name, :surname, :favorites
  end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
  bin/rake generate scaffold favorites movies:references profiles:references
  ```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
  Break down the relationship for one of the two main entities. We will use it in join table only.
  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md
  One-to-many example, In a databse in school, One advisor has many students and one student only has one advisor.
  Many-to-many example, One course has many students, and one studnet has many courses. 
  ```
