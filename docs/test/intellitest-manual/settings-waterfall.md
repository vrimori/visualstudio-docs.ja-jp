---
title: 設定ウォーターフォール | Microsoft IntelliTest 開発者テスト ツール | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9265fd0ada4f966f5d5fba01591e10f5f0a4194f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="settings-waterfall"></a>設定ウォーターフォール

設定ウォーターフォールの概念とは、ユーザーが**アセンブリ**、**フィクスチャ**、**探索**レベルで設定を指定できることを意味します。 

* アセンブリ - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* フィクスチャ - [PexClass](attribute-glossary.md#pexclass)
* 探索 - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

**アセンブリ** レベルで指定された設定は、そのアセンブリの下にあるすべてのフィクスチャと探索に影響を与えます。 **フィクスチャ** レベルで指定された設定は、そのフィクスチャの下にあるすべての探索に影響を与えます。 子設定 win: 設定が**アセンブリ** レベルと**フィクスチャ** レベルで定義されている場合、**フィクスチャ**設定が使用されます。

一部の設定は**アセンブリ** レベルまたは**フィクスチャ** レベルに固有となります。 

**例**

```
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500 
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>フィードバックをお寄せください

ご意見や機能に関するご要望を **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** で投稿してください。
