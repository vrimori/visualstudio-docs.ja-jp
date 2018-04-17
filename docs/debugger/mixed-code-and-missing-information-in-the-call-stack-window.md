---
title: 混合コードと呼び出し履歴 ウィンドウで不足している情報 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 580fc3b87173a120480f708e8b349fbb6942bbdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>[呼び出し履歴] ウィンドウの混合コードと不足情報
マネージ コードとネイティブ コードの呼び出し履歴には違いがあるため、コードの種類が混在する場合、呼び出し履歴にすべてを表示できるとは限りません。 以下の不具合に気付くかもしれませんネイティブ コードがマネージ コードを呼び出すと、**呼び出し履歴**ウィンドウ。  
  
-   マネージ コードのすぐ上にあるネイティブ フレームがない可能性があります、**呼び出し履歴**ウィンドウです。 詳細については、次を参照してください。[する方法: ネイティブ フレームが呼び出し履歴 ウィンドウから不足ときにマネージ コードからステップ](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)です。  
  
-   デバッガーの外部で起動された混合モード アプリケーション、**呼び出し履歴**ウィンドウがマネージ コードのみを表示し、いずれかのネイティブ フレームが表示されます。  
  
 上の 2 つの不具合はめったに発生しません。 ネイティブ コードによるマネージ コードの呼び出しでは、ほとんどの場合、正しい呼び出し履歴が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法 : [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)