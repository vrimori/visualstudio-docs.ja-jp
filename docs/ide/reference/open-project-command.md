---
title: OpenProject コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>OpenProject コマンド
既存のプロジェクトを開きます。

## <a name="syntax"></a>構文

```
File.OpenProject filename
```

## <a name="arguments"></a>引数
 `filename`

 必須。 開くプロジェクトの完全パスとファイル名。

 `filename` 引数の構文の場合、空白を含むパスで引用符を使用する必要があります。

## <a name="remarks"></a>コメント
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。

 デバッグ中にこのコマンドを使用することはできません。

## <a name="example"></a>例
 この例では、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトの Test1 を開きます。

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)