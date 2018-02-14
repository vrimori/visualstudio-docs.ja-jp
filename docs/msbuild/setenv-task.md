---
title: "SetEnv タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ffcbbff4b04bcfa48fdf4d4812be033c659322af
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="setenv-task"></a>SetEnv タスク
指定された環境変数の値を設定または削除します。  
  
## <a name="parameters"></a>パラメーター  
 **SetEnv** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**Name**|必須の **String** 型のパラメーターです。<br /><br /> 環境変数の名前。|  
|**OutputEnvironmentVariable**|省略可能な **String** 型の出力パラメーターです。<br /><br /> **Name** パラメーターによって指定される環境変数に割り当てられる値が含まれます。|  
|**Prefix**|必須の `Boolean` パラメーターです。<br /><br /> `true` の場合、**Name** パラメーターによって指定される環境変数値の前に **Value** パラメーターの値を連結し、結果を環境変数に割り当てます。 `false` の場合、**Value** パラメーターの値のみを環境変数に割り当てます。|  
|**Target**|省略可能な **String** 型のパラメーターです。<br /><br /> 環境変数が保存される場所を指定します。 "`User`" または "`Machine`" を指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの "EnvironmentVariableTarget Enumeration" (EnvironmentVariableTarget 列挙型) をご覧ください|  
|**[値]**|省略可能な **String** 型のパラメーターです。<br /><br /> **Name** パラメーターによって指定される環境変数に割り当てられる値。 **Value** が空で変数が存在する場合、変数が削除されます。 変数が存在しない場合、操作が実行できなくてもエラーは発生しません。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの "Environment::SetEnvironmentVariable Method" (Environment::SetEnvironmentVariable メソッド) を参照してください。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)