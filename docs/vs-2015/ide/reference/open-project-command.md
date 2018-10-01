---
title: OpenProject コマンド | Microsoft Docs
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
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8f70d5605f4ee47171992e3a94c145cbdc8785
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533649"
---
# <a name="open-project-command"></a>OpenProject コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[開いているプロジェクト コマンド](https://docs.microsoft.com/visualstudio/ide/reference/open-project-command)します。  
  
  
既存のプロジェクトを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須。 開くプロジェクトの完全パスとファイル名。  
  
 `filename` 引数の構文の場合、空白を含むパスで引用符を使用する必要があります。  
  
## <a name="remarks"></a>Remarks  
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。  
  
 デバッグ中にこのコマンドを使用することはできません。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] プロジェクトの Test1 を開きます。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)



