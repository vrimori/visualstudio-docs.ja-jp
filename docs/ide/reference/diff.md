---
title: -Diff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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