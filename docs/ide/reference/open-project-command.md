---
title: OpenProject コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ba474de9c422031562e97d871cc070365f993cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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