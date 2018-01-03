---
title: "GenerateTrustInfo タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 614ace0800393b6c584da4cf4d85edfa7ea11b33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo タスク
基本マニフェスト、`TargetZone` パラメーター、および `ExcludedPermissions` パラメーターからアプリケーションの信頼を生成します。  
  
## <a name="parameters"></a>パラメーター  
 `GenerateTrustInfo` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`ApplicationDependencies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 依存アセンブリを指定します。|  
|`BaseManifest`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーションの信頼を生成する基本マニフェストを指定します。|  
|`ExcludedPermissions`|省略可能な `String` 型のパラメーターです。<br /><br /> ゾーンの既定のアクセス許可セットから除外する、セミコロンで区切られた 1 つまたは複数のアクセス許可 ID 値を指定します。|  
|`TargetZone`|省略可能な `String` 型のパラメーターです。<br /><br /> コンピューター ポリシーから取得される、ゾーンの既定のアクセス許可セットを指定します。|  
|`TrustInfoFile`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型の出力パラメーターです。<br /><br /> アプリケーション セキュリティ信頼情報が含まれるファイルを指定します。|  
  
## <a name="remarks"></a>コメント  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は <xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)