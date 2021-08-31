# 7) Relationships:



# NOTE:

Don't call the primary key **`id`**, **`Id`** or **`ID`**


# 1) One To Many:



<b>



**`Models/Post.cs`**


```cs
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;


namespace Application.Models
{
    public class Post
    {
        public int PostId { get; set; }
        public string Content { get; set; }

        public List<Comment> Comments { get; set; }

    }
}
```




**`Models/Comment.cs`**

```cs
using System;
using System.ComponentModel.DataAnnotations;

namespace Application.Models
{
    public class Comment
    {
        public int CommentId { get; set; }

        public string Content { get; set; }

        public int PostId { get; set; }
        public Post Post { get; set; }

    }
}
```




CLI:

```sh
dotnet ef migrations add <migration name>
dotnet ef migrations list
dotnet ef database update
```




</b>
