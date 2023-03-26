# 选择新的主密码

> 原文：<https://medium.com/swlh/choosing-a-new-master-password-cdefe31dff3c>

多年来，我一直想改变和改进我的主密码。我*知道*的步骤，但我真的希望有人为我拼写出来，所以我会为你拼写出具体的步骤。

![](img/38bf6bd3885d38f7b4bd3595c2752583.png)

Photo by [Cristina Gottardi](https://unsplash.com/photos/maaWpQVgi00)

流行的密码管理器通过维护一个包含许多秘密的加密数据库来工作，由*主密码*和访问加密数据库文件的组合来保护，该加密数据库文件在您的设备之间同步。选择一个强有力的主密码是至关重要的，以防你的设备被盗或托管你的密码文件的云存储被破坏。

# 1.高熵记忆密码短语

我推荐这款发电机:
[https://github.com/redacted/XKCD-password-generator](https://github.com/redacted/XKCD-password-generator)

它是用 Python 写的，它有很好的默认值，和一个明智的内置单词词典(65，355 个单词)。可以用`pip install xkcdpass`安装。

您可以使用各种命令行标志来调整长度和公式。我建议获取一大堆密码，并从列表中直观地选择一个。

```
$ xkcdpass --count=100
jewelweed cruzeiro scrawny preempt edgeways ceramist
vendor sacker someone elevator jeweled croaky
ammonia American bunk bed rhymer velleity drenched
linger largesse plain thoraces withered big deal
Rolland wheelie empanada repossess colic hosteler
....
```

确保从列表中选择，而不是自己编造，因为人类在随机方面比我们直觉认为的要差得多。

# 2.写下来

是的，你应该把它写下来— **但是要确保它写在可以可靠销毁的东西上**并且在销毁之前不会被发现。一张你可以撕掉或烧掉的纸就可以了。确保它的安全，直到你准备好销毁它。

**完全可选:**如果你雄心勃勃，现在是时候通过添加一些随机的符号和数字来增加它了。**避免常见的字母替换，如**[**l33t speak**](https://en.wikipedia.org/wiki/Leet)因为每个密码破解工具都会自动尝试这些现成的。挑选几个随机的数字和符号，把它们放在你的一些单词中间。

在已经随机的密码中增加随机性是可以的，但是要避免通过用你一时兴起选择的单词替换你的随机单词或者简化一般短语来消除随机性。

如果您不确定该怎么做，那么就保留 xkcdpass 中的密码短语。这样很好，你不想让它太难记住。

# 3.记忆和练习

用短信制作一个文本文件，并用新密码加密。我喜欢使用流行的包管理器中提供的 [scrypt](https://www.tarsnap.com/scrypt.html) :

```
$ brew install scrypt  # or apt-get install scrypt
$ echo "I remembered my password" > pwtest.txt
$ scrypt enc pwtest.txt > pwtest.enc
Please enter passphrase:
...
$ rm pwtest.txt  # Don't need this anymore
```

现在我们有了加密的测试文件，我们可以练习解锁它，直到我们记住密码:

```
$ scrypt dec pwtest.enc
Please enter passphrase:
...
I remembered my password
$ scrypt dec pwtest.enc
Please enter passphrase:
...
I remembered my password
$ scrypt dec pwtest.enc
Please enter passphrase:
...
I remembered my password
```

如果您喜欢使用 GPG 而不是 scrypt:

```
$ echo "I remembered my password" > pwtest.txt
$ gpg -c pwtest.txt
Enter passphrase:
...
$ gpg pwtest.txt.gpg
Enter passphrase:
...
I remembered my password
```

# 4.采用新的主密码

在练习了几天你的新密码后，是时候采用它了:销毁你写在上面的纸，更改你的密码管理器的主密码，并记住:**永远不要在其他任何地方使用你的主密码。**

主密码是用来保护其他密码安全的。它永远不应该被用作另一个帐户的密码，即使它是你的银行或 iCloud 或其他什么。**主密码是给你的密码管理器**用的，你必须使用你的密码管理器生成并保存你其余账户的密码。

如果你还没有使用密码管理器，我推荐你使用[1 密码](https://1password.com/)。它是付费的，但在大多数平台上与原生客户端非常完美。

如果你需要一些免费和开源的东西，那么 KeePass 是一个不错的选择，每个平台上都有可用的客户端。

# 良好的安全卫生

*   使用随机生成的强密码作为您的主密码。
    **干得好，干得好。**
*   使用密码管理器。
    **希望已经完成？**
*   为您的所有设备和服务启用加密。
    **尤其是你可能会丢失的便携式设备，比如手机和笔记本电脑。**
*   选择使用自带良好安全默认设置的应用程序。**并非所有的安全性或加密都是同等的:**安全性差的应用程序就像密码不正确的帐户。有时，糟糕的安全性可能比没有安全性更糟糕，如果它设法哄骗您产生错误的期望。

你不会后悔良好的安全卫生，尤其是在网络不断加剧的情况下。