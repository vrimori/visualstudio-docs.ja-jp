---
title: "Message タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 23
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: e2c4a65b44ea3cdc9ed54911e8037467e5ce5554
ms.lasthandoff: 02/22/2017

---
# <a name="message-task"></a>Message タスク
ビルド中のメッセージをログに記録します。  
  
## <a name="parameters"></a>パラメーター  
 `Message` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Importance`|省略可能な `String` 型のパラメーターです。<br /><br /> メッセージの重要度を指定します。 このパラメーターの値には、`high`、`normal`、または `low` を指定できます。 既定値は `normal` です。|  
|`Text`|省略可能な `String` 型のパラメーターです。<br /><br /> ログに記録するエラー テキスト。|  
  
## <a name="remarks"></a>コメント  
 `Message` タスクを使用すると、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトで、ビルド処理のさまざまな段階でロガーにメッセージを発行できます。  
  
 `Condition` パラメーターが `true` と評価されると、`Text` パラメーターの値がログに記録され、ビルド処理が継続されます。 `Condition` パラメーターが存在しない場合は、メッセージ テキストがログに記録されます。 ログ処理の詳細については、[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)に関するページを参照してください。  
  
 既定では、メッセージは MSBuild のコンソール ロガーに送信されます。 これは、<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> パラメーターを設定することで変更できます。 ロガーによって `Importance` パラメーターが解釈されます。  
  
 このタスクでは、上記のパラメーター以外に、<xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承し、このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加パラメーター一覧とそれらの説明については、「[TaskExtension Base Class (TaskExtension 基底クラス)](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例は、登録されているすべてのロガーにメッセージをログ記録します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)
