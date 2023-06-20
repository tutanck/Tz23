# User

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

# Group

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

# Usecases

## user usecase

const user = findUserById(params.id);

const userGroups = findGroupsByQuery({ author: user.id });

## user groups from user usecase

const userGroups = findGroupsByQuery({ author: params.id });

## user groups from groups usecase

const userWithTheirGroups = findUserById(params.id, null, {
populate: { path: "groups" },
});
