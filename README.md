# DemoTz

## User

```Javascript
{
  "groups": {
    "ref": "Group",
    "required": true,
    "type": "ObjectId"
  },
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

## Usecase (get user's groups)

### from user

```Javascript
const user = findUserById(params.id);

const userGroups = findGroupsByQuery({ author: user.id });

```

### from params (user's id)

```Javascript
const userGroups = findGroupsByQuery({ author: params.id });
```

### From populated user

```Javascript
const userWithTheirGroups = findUserById(params.id, null, {
    populate: { path: "groups" },
});
```

### How it works

![alt text](https://github.com/tutanck/Tz23/blob/main/How_it_works.jpg)

### Open FeedBack

![alt text](https://github.com/tutanck/Tz23/blob/main/Tz23QRCode.png)
