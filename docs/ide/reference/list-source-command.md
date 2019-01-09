---
title: List Source コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7a94af10921c80b87b7d53f0f587aaf9ca55b22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850362"
---
# <a name="list-source-command"></a>List Source コマンド
ソース コードの指定行が表示されます。

## <a name="syntax"></a>構文

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>スイッチ
 /Count:`number`

 任意。 表示する行数を指定します。

 /Current

 任意。 現在の行を表示します。

 /File:`filename`

 任意。 表示するファイルのパス。 ファイル名が指定されていない場合は、現在のステートメントの行のソース コードが表示されます。

 /Line:`number`

 任意。 特定の行番号を表示します。

 /ShowLineNumbers:`yes|no`

 任意。 行番号を表示するかどうかを指定します。

## <a name="example"></a>例
 この例では、Form1.vb ファイルの 4 行目からソース コードが行番号付きでリストされます。

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>「

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)