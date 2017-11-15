---
title: "設定ウォーターフォール | Microsoft IntelliTest 開発者テスト ツール | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Settings waterfall
ms.assetid: 45777037-9E16-4ABF-BD26-5AF4E740D4E6
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: fda01f53c02c0de03e69b65287dd627bf4a786e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
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
