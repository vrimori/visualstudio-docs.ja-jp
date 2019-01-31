---
title: プロジェクトを開くコマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14ca6ed2f9a3e21d641f9d5dbe83234066886164
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010169"
---
# <a name="open-project-command"></a>OpenProject コマンド

既存のプロジェクトやソリューションを開きます。

## <a name="syntax"></a>構文

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>引数

`filename`

必須です。 開くプロジェクトまたはソリューションの完全パスとファイル名。

> [!NOTE]
> `filename` 引数の構文の場合、空白を含むパスで引用符を使用する必要があります。

## <a name="remarks"></a>コメント

オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。

デバッグ中にこのコマンドを使用することはできません。

## <a name="example"></a>例

次の例では、Visual Basic プロジェクト **Test1** が開きます。

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>関連項目

- [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [[検索/コマンド] ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)