---
title: "既存プロジェクトの追加コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e41dd319e00dccbc180319bf3642c665cf4df58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="add-existing-project-command"></a>AddExistingProject コマンド
既存のプロジェクトを現在のソリューションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 省略可能です。 ソリューションに追加するプロジェクトの完全なパスとプロジェクト名 (拡張子付き)。  
  
 `filename` 引数にスペースが含まれる場合は、引用符で囲む必要があります。  
  
 ファイル名が指定されていない場合、ファイルを開くダイアログ ボックスが表示され、ユーザーがプロジェクトを選択できます。  
  
## <a name="remarks"></a>コメント  
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトの TestProject1 を現在のソリューションに追加します。  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)