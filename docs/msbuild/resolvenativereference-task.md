---
title: "ResolveNativeReference タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b0b08a9602c81e504bf2cd01d1d1ce9720dc6b2a
ms.lasthandoff: 02/22/2017

---
# <a name="resolvenativereference-task"></a>ResolveNativeReference タスク
ネイティブ参照を解決します。 <xref:Microsoft.Build.Tasks.ResolveNativeReference> クラスを実装します。 このクラスは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `ResolveNativeReference` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|必須の [String](assetId:///String?qualifyHint=False&autoUpgrade=True)`[]` 型のパラメーターです。<br /><br /> ネイティブ参照のアセンブリ ID を解決するための検索パスを取得または設定します。|  
|`ContainedComComponents`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリの COM コンポーネントを取得または設定します。|  
|`ContainedLooseEtcFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ マニフェストに示されているルース Etc ファイルを取得または設定します。|  
|`ContainedLooseTlbFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリの Loose .tlb ファイルを取得または設定します。|  
|`ContainedPrerequisiteAssemblies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> マニフェストを使用する前に存在する必要があるアセンブリを取得または設定します。|  
|`ContainedTypeLibraries`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> ネイティブ アセンブリのタイプ ライブラリを取得または設定します。|  
|`ContainingReferenceFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーターです。<br /><br /> 参照ファイルを取得または設定します。|  
|`NativeReferences`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> Win32 ネイティブ アセンブリ参照を取得または設定します。|  
  
## <a name="remarks"></a>コメント  
 このタスクでは、上記のパラメーター以外に、<xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承し、このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加パラメーター一覧とそれらの説明については、「[TaskExtension Base Class (TaskExtension 基底クラス)](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)
