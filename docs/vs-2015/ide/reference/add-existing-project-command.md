---
title: 既存プロジェクトの追加コマンド | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 048ba8e43b66ac5ad4bbc1d0c09adb75a2d61e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534343"
---
# <a name="add-existing-project-command"></a>AddExistingProject コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[既存プロジェクトの追加コマンド](https://docs.microsoft.com/visualstudio/ide/reference/add-existing-project-command)します。  
  
  
既存のプロジェクトを現在のソリューションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 任意。 ソリューションに追加するプロジェクトの完全なパスとプロジェクト名 (拡張子付き)。  
  
 `filename` 引数にスペースが含まれる場合は、引用符で囲む必要があります。  
  
 ファイル名が指定されていない場合、ファイルを開くダイアログ ボックスが表示され、ユーザーがプロジェクトを選択できます。  
  
## <a name="remarks"></a>Remarks  
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] プロジェクトの TestProject1 を現在のソリューションに追加します。  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)



