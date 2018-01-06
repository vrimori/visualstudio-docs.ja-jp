---
title: "混合コードと呼び出し履歴 ウィンドウで不足している情報 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a234529f13217cabf59a8d3827427e2f5341fb53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>[呼び出し履歴] ウィンドウの混合コードと不足情報
マネージ コードとネイティブ コードの呼び出し履歴には違いがあるため、コードの種類が混在する場合、呼び出し履歴にすべてを表示できるとは限りません。 以下の不具合に気付くかもしれませんネイティブ コードがマネージ コードを呼び出すと、**呼び出し履歴**ウィンドウ。  
  
-   マネージ コードのすぐ上にあるネイティブ フレームがない可能性があります、**呼び出し履歴**ウィンドウです。 詳細については、次を参照してください。[する方法: ネイティブ フレームが呼び出し履歴 ウィンドウから不足ときにマネージ コードからステップ](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)です。  
  
-   デバッガーの外部で起動された混合モード アプリケーション、**呼び出し履歴**ウィンドウがマネージ コードのみを表示し、いずれかのネイティブ フレームが表示されます。  
  
 上の 2 つの不具合はめったに発生しません。 ネイティブ コードによるマネージ コードの呼び出しでは、ほとんどの場合、正しい呼び出し履歴が表示されます。  
  
## <a name="see-also"></a>参照  
 [方法 : [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)