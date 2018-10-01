---
title: 混合コードと不足情報、呼び出し履歴 ウィンドウ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c91b2e49dc94057ab7929380ad1b819cd01731d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539210"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>[呼び出し履歴] ウィンドウの混合コードと不足情報
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[の混合コードと不足情報呼び出し履歴 ウィンドウで](https://docs.microsoft.com/visualstudio/debugger/mixed-code-and-missing-information-in-the-call-stack-window)します。  
  
マネージド コードとネイティブ コードの呼び出し履歴には違いがあるため、コードの種類が混在する場合、呼び出し履歴にすべてを表示できるとは限りません。 ネイティブ コードでは、マネージ コードを呼び出しで以下の不具合がわかりますが、**呼び出し履歴**ウィンドウ。  
  
-   マネージ コードのすぐ上にあるネイティブ フレームがない可能性があります、**呼び出し履歴**ウィンドウ。 詳細については、次を参照してください。[方法: ネイティブ フレームが呼び出し履歴 ウィンドウから不足しているときに、マネージ コードからステップ](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)します。  
  
-   デバッガーの外部で起動された混合モード アプリケーション、**呼び出し履歴**ウィンドウがマネージ コードのみを表示し、いずれかのネイティブ フレームが表示されます。  
  
 上の 2 つの不具合はめったに発生しません。 ネイティブ コードによるマネージド コードの呼び出しでは、ほとんどの場合、正しい呼び出し履歴が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法 : [呼び出し履歴] ウィンドウを使用する](../debugger/how-to-use-the-call-stack-window.md)





