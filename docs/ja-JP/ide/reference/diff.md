---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diff
2 つのファイルを比較します。 相違点は特殊な Visual Studio のウィンドウに表示されます。

## <a name="syntax"></a>構文

```
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>引数
 `SourceFile`

 必須。 比較する最初のファイルの完全パスと名前。

 `TargetFile`

 必須。 比較する 2 番目のファイルの完全パスと名前。

 `SourceDisplayName`

 任意。 最初のファイルの表示名。

 `TargetDisplayName`

 任意。 2 番目のファイルの表示名。