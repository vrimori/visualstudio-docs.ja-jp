---
title: GetReferenceAssemblyPaths タスク | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 619a533e1bdbdec00e631aac64d6ddf84bf161c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535051"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[GetReferenceAssemblyPaths タスク](https://docs.microsoft.com/visualstudio/msbuild/getreferenceassemblypaths-task)します。  
  
  
各種フレームワークの参照アセンブリのパスを返します。  
  
## <a name="parameters"></a>パラメーター  
 `GetReferenceAssemblyPaths` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|省略可能な `String[]` 型の出力パラメーターです。<br /><br /> `TargetFrameworkMoniker` パラメーターに基づいて、パスを返します。 `TargetFrameworkMoniker` が null または空の場合、このパスは `String.Empty` になります。|  
|`FullFrameworkReferenceAssemblyPaths`|省略可能な `String[]` 型の出力パラメーターです。<br /><br /> モニカーのプロファイル部分を考慮せず、`TargetFrameworkMoniker` パラメーターに基づいて、パスを返します。 `TargetFrameworkMoniker` が null または空の場合、このパスは `String.Empty` になります。|  
|`TargetFrameworkMoniker`|省略可能な `String` 型のパラメーターです。<br /><br /> 参照アセンブリ パスに関連付けられているターゲット フレームワーク モニカーを指定します。|  
|`RootPath`|省略可能な `String` 型のパラメーターです。<br /><br /> 参照アセンブリ パスの生成に使用するルート パスを指定します。|  
|`BypassFrameworkInstallChecks`|(省略可能) [ブール] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) パラメーター。<br /><br /> `true` の場合、ターゲット フレームワークに応じて、特定のランタイム フレームワークがインストールされるように既定で `GetReferenceAssemblyPaths` が実行する基本的なチェックを省略します。|  
|`TargetFrameworkMonikerDisplayName`|省略可能な `String` 型の出力パラメーターです。<br /><br /> ターゲット フレームワーク モニカーの表示名を指定します。|  
  
## <a name="remarks"></a>Remarks  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



