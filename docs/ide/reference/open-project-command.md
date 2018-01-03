---
title: "OpenProject コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6ae2b8f0c9f0a17f29bf42a8a2893f8671df4cd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="open-project-command"></a>OpenProject コマンド
既存のプロジェクトを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須。 開くプロジェクトの完全パスとファイル名。  
  
 `filename` 引数の構文の場合、空白を含むパスで引用符を使用する必要があります。  
  
## <a name="remarks"></a>コメント  
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。  
  
 デバッグ中にこのコマンドを使用することはできません。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトの Test1 を開きます。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)