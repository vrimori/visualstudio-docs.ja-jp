---
title: 混合コードと不足情報、呼び出し履歴 ウィンドウ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 7f0a0822dc99eccea4ddd621ae622a112e0909bb
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151985"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>[呼び出し履歴] ウィンドウの混合コードと不足情報
マネージド コードとネイティブ コードの呼び出し履歴には違いがあるため、コードの種類が混在する場合、呼び出し履歴にすべてを表示できるとは限りません。 ネイティブ コードでは、マネージ コードを呼び出しで以下の不具合がわかりますが、**呼び出し履歴**ウィンドウ。  
  
-   マネージ コードのすぐ上にあるネイティブ フレームがない可能性があります、**呼び出し履歴**ウィンドウ。 詳細については、次を参照してください。[方法: ネイティブ フレームが呼び出し履歴 ウィンドウから不足しているときに、マネージ コードからステップ](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)します。  
  
-   デバッガーの外部で起動された混合モード アプリケーション、**呼び出し履歴**ウィンドウがマネージ コードのみを表示し、いずれかのネイティブ フレームが表示されます。  
  
 上の 2 つの不具合はめったに発生しません。 ネイティブ コードによるマネージド コードの呼び出しでは、ほとんどの場合、正しい呼び出し履歴が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法 : [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)