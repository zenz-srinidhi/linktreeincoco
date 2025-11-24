# LinkTree on Coco (MOI Blockchain)

A simple decentralized version of **LinkTree**, built using **Coco language** on the **MOI blockchain**.

Each user (actor) can create:
- A **public username**
- A **profile** (name, bio, avatar)
- A **list of links**
- A **click counter** for each link

All data is stored **on-chain** inside the actor's private context.

---

## 🚀 Features

- **Create profile** (name, bio, avatar, username)
- **Add / delete links**
- **Public view**:  
  `GetPublicProfile(username)`  
  `GetPublicLinks(username)`
- **Click tracking**
- **Simple & clean Coco implementation**

---

## 📦 Project Structure

```
linktree.coco → Coco logic (smart contract)
coco.nut → Build configuration
```

---

## 🧠 Storage Model

### Logic State (Global)

| Key | Type | Description |
|-----|------|-------------|
| `usernames` | Map[String]Identifier | `username → actor` |
| `clicks` | Map[String]U64 | `"username:index" → click count` |

### Actor State (Per User)

| Key | Type | Description |
|-----|------|-------------|
| `profile` | Profile | User profile |
| `links` | []Link | User's list of links |

---

## 📚 Usage Flow

### 1️⃣ Deploy Logic

```sh
deploy LinkTree.Init()
```

### 2️⃣ Enlist User (initialize actor state)

```sh
enlist LinkTree.InitUser()
```

### 3️⃣ Set Your Profile

```sh
invoke LinkTree.SetProfile(
    name: "Srinidhi",
    bio: "Frontend Dev",
    avatar: "",
    username: "srinidhi"
)
```

### 4️⃣ Add Links

```sh
invoke LinkTree.AddLink(title: "GitHub", url: "github.com")
invoke LinkTree.AddLink(title: "YouTube", url: "youtube.com")
```

### 5️⃣ Delete a Link

```sh
invoke LinkTree.DeleteLink(index: 0)
```

### 6️⃣ View Your Data

```sh
invoke LinkTree.GetMyProfile()
invoke LinkTree.GetMyLinks()
```

### 🌍 Public Access (LinkTree-style)

These endpoints allow anyone to view a user's public page.

#### Get Profile

```sh
invoke LinkTree.GetPublicProfile(username: "srinidhi")
```

#### Get Links

```sh
invoke LinkTree.GetPublicLinks(username: "srinidhi")
```

#### Record Click

```sh
invoke LinkTree.RecordClick(username: "srinidhi", index: 0)
```

#### Get Click Count

```sh
invoke LinkTree.GetClickCount(username: "srinidhi", index: 0)
```

---

## 🛠 Compile

```sh
coco compile
```

---

## ✔️ Requirements

- Coco compiler installed
- MOI Cocolab environment

---

## 📄 License

MIT License