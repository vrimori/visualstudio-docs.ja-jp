---
title: -Diff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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