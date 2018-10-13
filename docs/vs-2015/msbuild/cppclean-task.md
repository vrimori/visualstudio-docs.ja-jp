---
title: CPPClean タスク | Microsoft Docs
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
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4d7472a92818987a5dd0257d1aa33ac80532e12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255815"
---
# <a name="cppclean-task"></a>CPPClean タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ プロジェクトのビルド時に MSBuild によって作成される一時ファイルを削除します。 ビルド ファイルを削除するプロセスは、*クリーニング* と呼ばれます。  
  
## <a name="parameters"></a>パラメーター  
 **CPPClean** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**DeletedFiles**|省略可能な `ITaskItem[]` 型の出力パラメーターです。<br /><br /> タスクで使用および生成できる MSBuild 出力ファイル項目の配列を定義します。|  
|**DoDelete**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合は、一時ビルド ファイルを消去します。|  
|**FilePatternsToDeleteOnClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するファイルのファイル拡張子をセミコロンで区切ったリストを指定します。|  
|**FilesExcludedFromClean**|省略可能な `String` 型のパラメーターです。<br /><br /> 消去しないファイルをセミコロンで区切ったリストを指定します。|  
|**FoldersToClean**|必須の `String` 型のパラメーターです。<br /><br /> 消去するディレクトリをセミコロンで区切ったリストを指定します。 完全パスまたは相対パスを指定することができ、パスにはワイルドカード記号 (**\***) を含めることができます。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)



