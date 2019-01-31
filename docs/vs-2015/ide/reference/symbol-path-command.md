---
title: Symbol Path コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da136a76a06182bd32ebf2ca868e77f202087e45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767284"
---
# <a name="symbol-path-command"></a>Symbol Path コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
デバッガーによってシンボルが検索されるディレクトリの一覧を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>引数  
 `pathname`  
 任意。 デバッガーによってシンボルが検索されるパスを、セミコロンで区切った一覧です。  
  
## <a name="remarks"></a>コメント  
 `pathname` を指定しない場合、シンボル用の現在のパスがコマンドによって一覧表示されます。  
  
## <a name="example"></a>例  
 次の例では、シンボル ディレクトリの一覧に 2 つのパスを追加します。  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>例  
 次の例では、シンボル用の現在のパスをセミコロンで区切った一覧が表示されます。  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>「  
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
