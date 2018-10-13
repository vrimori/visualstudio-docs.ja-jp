---
title: GetFrameworkPath タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcad656c058fffaf3f075b195cb1f105079a8e5d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248600"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] アセンブリへのパスを取得します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `GetFrameworkPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 存在する場合、フレームワーク バージョン 1.1 アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
|`FrameworkVersion20Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 存在する場合、フレームワーク バージョン 2.0 アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
|`FrameworkVersion30Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 存在する場合、フレームワーク バージョン 3.0 アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
|`FrameworkVersion35Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 存在する場合、フレームワーク バージョン 3.5 アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
|`FrameworkVersion40Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 存在する場合、フレームワーク バージョン 4.0 アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
|`Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 利用できる場合、最新のフレームワーク アセンブリのパスが含まれます。 それ以外の場合は、`null` を返します。|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] のいくつかのバージョンがインストールされている場合、このタスクは、[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] が実行されるように設計されているバージョンを返します。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`GetFrameworkPath` タスクを使用し、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] のパスを `FrameworkPath` プロパティに保存します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



