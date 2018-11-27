---
title: JIT の最適化とデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab86e023b99f524651b56bbca4ddea2d613448e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770748"
---
# <a name="jit-optimization-and-debugging"></a>JIT の最適化とデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

マネージ アプリケーションをデバッグするときに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]既定 - イン タイム (JIT) コードの最適化を抑制します。 JIT 最適化の省略とは、最適化されていないコードをデバッグすることを示します。 最適化されていないため、コードの実行速度はやや遅くなりますが、デバッグで操作できる内容はより詳細になります。 最適化されたコードをデバッグするのは困難であるため、最適化されたコードで発生するバグが、非最適化バージョンでは再現しないときにのみお勧めします。  
  
 JIT の最適化が制御されます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]によって、**モジュールの読み込みで抑制の JIT 最適化**オプション。 このオプションを見つけることができます、**全般**ページで、**デバッグ**内のノード、**オプション** ダイアログ ボックス。  
  
 オフにした場合、**モジュールの読み込みで抑制の JIT 最適化**オプション、最適化された JIT コードをデバッグすることができますが、最適化されたコードがソース コードと一致しないために、デバッグ機能が限られた可能性があります。 その結果、デバッガー ウィンドウをなど、**ローカル**と **[自動変数]** ウィンドウは最適化されていないコードをデバッグしていた場合に、できるだけ多くの情報が表示されません。  
  
 もう 1 つの重要な違いは、マイ コードのみを使用したデバッグの問題です。 マイ コードのみでデバッグすると、デバッガーでは、最適化されたコードはユーザー コードではないと見なされ、これらのコードはデバッグ中に表示されません。 このため、JIT の最適化されたコードをデバッグする場合でも、マイ コードのみをオフに切り替えるという選択肢も考えられます。 詳細については、次を参照してください。[ステップ実行をマイ コードのみに制限する](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code)します。  
  
 注意して、**モジュールの読み込みで抑制の JIT 最適化**モジュールが読み込まれるときに、オプションがコードの最適化を抑制します。 実行中のプロセスにアタッチする場合、既に読み込まれ、JIT でコンパイルされ、最適化されているコードが含まれることがあります。 **モジュールの読み込みで抑制の JIT 最適化**オプションには、このようなコードへの影響はありませんアタッチした後に読み込まれたモジュールには影響が。 さらに、**モジュールの読み込みで抑制の JIT 最適化**オプションではアセンブリを NGEN で作成された WinForms.dll などのモジュールには影響しません。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)   
 [実行中のプロセスをアタッチします。](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [マネージド実行プロセス](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)



