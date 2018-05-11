---
title: Warning タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51c717cc1bc744438afd277e5f154fdcd8852e8d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="warning-task"></a>Warning タスク
条件付きステートメントの評価に基づいてビルド中の警告をログに記録します。  
  
## <a name="parameters"></a>パラメーター  
 `Warning` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Code`|省略可能な `String` 型のパラメーターです。<br /><br /> 警告に関連付ける警告コード。|  
|`File`|省略可能な `String` 型のパラメーターです。<br /><br /> 関連ファイルが存在する場合、それを指定します。 ファイルが指定されない場合、Warning タスクを含むファイルが使用されます。|  
|`HelpKeyword`|省略可能な `String` 型のパラメーターです。<br /><br /> 警告に関連付けるヘルプ キーワード。|  
|`Text`|省略可能な `String` 型のパラメーターです。<br /><br /> `Condition` パラメーターが `true` と評価された場合に、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] がログに記録する警告テキストです。|  
  
## <a name="remarks"></a>コメント  
 `Warning` タスクでは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトは、次のビルド手順に進む前に、必要な構成の存在を確認できます。  
  
 `Warning` タスクの `Condition` パラメーターが `true` と評価される場合、`Text` パラメーターの値がログに記録され、ビルドが引き続き実行されます。 `Condition` パラメーターが存在しない場合は、警告テキストがログに記録されます。 ログ処理の詳細については、[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)に関するページを参照してください。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、コマンド ラインに設定されているプロパティが確認されます。 プロパティが設定されていない場合、警告イベントが生成され、`Warning` タスクの `Text` パラメーターの値がログに記録されます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>参照  
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)