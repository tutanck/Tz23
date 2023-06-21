# DemoTz

## Smallcode (intro)?

## User

```Javascript
{
  "groups": [
    {
      "ref": "Group",
      "required": true,
      "type": "ObjectId"
    }
  ],
  "email": {
    "required": true,
    "type": "String",
    "unique": true
  },
  "password": {
    "required": true,
    "type": "String"
  },
  "username": {
    "type": "String"
  }
}
```

## Group

```Javascript
{
  "author": {
    "ref": "User",
    "required": true,
    "type": "ObjectId"
  },
  "title": {
    "required": true,
    "type": "String",
    "unique": true
  },
  "about": {
    "type": "String"
  }
}
```

## Usecase: Create user

```Javascript
const user = createUser({
    email: body.email,
    password: body.pwd,
    username: body.uname
});
```

## Usecase: Add group to user

```Javascript
const user = findUserById(params.id);

const group = createGroup({
    author: user,
    about: body.about,
    title: body.title,
});

const updatedUser = updateUserById(user._id, {
    $push: { groups: [group] }
});
```

## Usecase: Get user's groups

### From params (user's id)

```Javascript
const userGroups = findGroupsByQuery({ author: params.id });
```

### From user

```Javascript
const user = findUserById(params.id);

const userGroups = findGroupsByQuery({ author: user._id });
```

### From populated user

```Javascript
const userWithItsGroups = findUserById(params.id, 'groups', {
    populate: { path: "groups" },
});
```

### How it works

![alt text](https://github.com/tutanck/Tz23/blob/main/How_it_works.jpg)

### Open FeedBack

![alt text](https://github.com/tutanck/Tz23/blob/main/Tz23QRCode.png)
