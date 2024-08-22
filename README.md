# README

Working through Ruby learnings.

https://www.theodinproject.com/lessons/ruby-on-rails-micro-reddit 

Instructions:

As before, add the associations you need between users, posts, and comments. You’ll need to be able to do the following methods successfully from the console (assuming your second user has an ID of 2):
> u2 = User.find(2)
> c1 = u2.comments.first should return that user’s comment. #comments returns an array with comments, which is why we need to use #first to actually retrieve the comment itself.
> c1.user should return that comment’s author User (u2).
> p1 = Post.first
> p1.comments.first should return the comment c1.
> c1.post should return the post p1.


Output:

u2 = User.find(2)
  User Load (0.3ms)  SELECT "users".* FROM "users" WHERE "users"."id" = ? LIMIT ?  [["id", 2], ["LIMIT", 1]]
=> #<User:0x00000001250b5ee8 id: 2, username: "jimbob", created_at: "2024-08-22 19:32:10.548856000 +0000", updated_at: "2024-08-22 19:32:10.548856000 +0000">
jp-micro-reddit(dev)> c1 = u2.comments.first
  Comment Load (0.2ms)  SELECT "comments".* FROM "comments" WHERE "comments"."user_id" = ? ORDER BY "comments"."id" ASC LIMIT ?  [["user_id", 2], ["LIMIT", 1]]
=> #<Comment:0x00000001252715e8 id: 2, user_id: 2, post_id: 1, body: "they really are!", created_at: "2024-08-22 19:33:07.083542000 +0000", updated_at: "2024-08-22 19:33:07.083542000 +0000">
jp-micro-reddit(dev)> c1 = u2.comments
  Comment Load (0.3ms)  SELECT "comments".* FROM "comments" WHERE "comments"."user_id" = ? /* loading for pp */ LIMIT ?  [["user_id", 2], ["LIMIT", 11]]
=> [#<Comment:0x0000000122c5a3c8 id: 2, user_id: 2, post_id: 1, body: "they really are!", created_at: "2024-08-22 19:33:07.083542000 +0000", updated_at: "2024-08-22 19:33:07.083542000 +0000">]
jp-micro-reddit(dev)> c1 = u2.comments.first
  Comment Load (0.3ms)  SELECT "comments".* FROM "comments" WHERE "comments"."user_id" = ? ORDER BY "comments"."id" ASC LIMIT ?  [["user_id", 2], ["LIMIT", 1]]
=> #<Comment:0x0000000122c75c90 id: 2, user_id: 2, post_id: 1, body: "they really are!", created_at: "2024-08-22 19:33:07.083542000 +0000", updated_at: "2024-08-22 19:33:07.083542000 +0000">
jp-micro-reddit(dev)> c1.user
=> #<User:0x00000001250b5ee8 id: 2, username: "jimbob", created_at: "2024-08-22 19:32:10.548856000 +0000", updated_at: "2024-08-22 19:32:10.548856000 +0000">
jp-micro-reddit(dev)> p1 = Post.first
  Post Load (0.3ms)  SELECT "posts".* FROM "posts" ORDER BY "posts"."id" ASC LIMIT ?  [["LIMIT", 1]]
=> #<Post:0x0000000124b158f8 id: 1, user_id: 1, body: "dogs are the best", created_at: "2024-08-22 19:21:17.092023000 +0000", updated_at: "2024-08-22 19:21:17.092023000 +0000">
jp-micro-reddit(dev)> p1.comments.first
  Comment Load (0.4ms)  SELECT "comments".* FROM "comments" WHERE "comments"."post_id" = ? ORDER BY "comments"."id" ASC LIMIT ?  [["post_id", 1], ["LIMIT", 1]]
=> #<Comment:0x0000000122c7bb90 id: 1, user_id: 1, post_id: 1, body: "test", created_at: "2024-08-22 19:30:02.656177000 +0000", updated_at: "2024-08-22 19:30:02.656177000 +0000">
jp-micro-reddit(dev)> c1.post
  Post Load (0.4ms)  SELECT "posts".* FROM "posts" WHERE "posts"."id" = ? LIMIT ?  [["id", 1], ["LIMIT", 1]]
=> #<Post:0x0000000122c7dd50 id: 1, user_id: 1, body: "dogs are the best", created_at: "2024-08-22 19:21:17.092023000 +0000", updated_at: "2024-08-22 19:21:17.092023000 +0000">