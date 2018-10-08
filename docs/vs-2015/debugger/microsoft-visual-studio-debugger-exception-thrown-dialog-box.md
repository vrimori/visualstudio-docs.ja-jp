---
title: Microsoft Visual Studio デバッガー (例外がスローされます) ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d2b27620cbc37bd771fff364d06a1a33d9c8b07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547410"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>[Microsoft Visual Studio デバッガー (例外がスローされました)] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Microsoft Visual Studio デバッガー (例外がスローされました) ダイアログ ボックス](https://docs.microsoft.com/visualstudio/debugger/microsoft-visual-studio-debugger-exception-thrown-dialog-box)します。  
  
プログラムに例外が発生しました。 このダイアログ ボックスには、スローされた例外の種類が報告されます。 コードでは、この例外を処理する必要があります。 この例外を処理するには、次のオプションから選択できます。  
  
 **Break**  
 デバッガーの実行を中断できます。 中断するまで、例外ハンドラーは起動されません。 中断した位置から継続すると、例外ハンドラーが起動されます。  
  
 **Continue**  
 実行が継続され、例外ハンドラーによって例外が処理されます。 このオプションは、特定の種類の例外に対しては使用できません。 **引き続き**アプリケーションを続行できるようになります。 ネイティブ アプリケーションでは、例外が再スローされます。 マネージド アプリケーションでは、プログラムが終了するか、または例外がホスト アプリケーションによって処理されます。  
  
> [!NOTE]
>  未処理の例外がマネージド コードで発生した後には実行を継続できません。 選択**続行**マネージ コードで未処理の例外とデバッグが停止した後。  
  
 **無視します。**  
 実行が継続されますが、例外ハンドラーは起動されません。 例外ハンドラーが起動されないため、例外やエラーなどが続けて発生することがあります。 このオプションは、特定の種類の例外に対しては使用できません。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでの例外を管理します。](../debugger/managing-exceptions-with-the-debugger.md)   
 [例外の推奨事項](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [例外処理](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)



