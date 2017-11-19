---
title: "JIT の最適化とデバッグ |Microsoft ドキュメント"
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
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>JIT の最適化とデバッグ
マネージ アプリケーションをデバッグするときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]既定・ イン タイム (JIT) コードの最適化を抑制します。 JIT 最適化の省略とは、最適化されていないコードをデバッグすることを示します。 最適化されていないため、コードの実行速度はやや遅くなりますが、デバッグで操作できる内容はより詳細になります。 最適化されたコードをデバッグするのは困難であるため、最適化されたコードで発生するバグが、非最適化バージョンでは再現しないときにのみお勧めします。  
  
 JIT 最適化を制御[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]によって、**モジュールの読み込みに抑制する状況の JIT 最適化を**オプション。 このオプションを見つけることができます、**全般**ページで、**デバッグ**内のノード、**オプション** ダイアログ ボックス。  
  
 オフにした場合、**モジュールの読み込みに抑制する状況の JIT 最適化を**オプション、最適化された JIT コードをデバッグすることができますが、最適化されたコードが、ソース コードと一致しないために、デバッグする機能が限定されることがあります。 その結果、デバッガーのウィンドウなど、**ローカル**と**[自動変数]**ウィンドウでは最適化されていないコードをデバッグしていた場合と同じ情報が表示されない場合があります。  
  
 もう 1 つの重要な違いは、マイ コードのみを使用したデバッグの問題です。 マイ コードのみでデバッグすると、デバッガーでは、最適化されたコードはユーザー コードではないと見なされ、これらのコードはデバッグ中に表示されません。 このため、JIT の最適化されたコードをデバッグする場合でも、マイ コードのみをオフに切り替えるという選択肢も考えられます。 詳細については、次を参照してください。[ステップ実行をマイ コードのみに制限する](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)です。  
  
 注意して、**モジュールの読み込みに抑制する状況の JIT 最適化を**オプションがモジュールが読み込まれるときに、コードの最適化を抑制します。 実行中のプロセスにアタッチする場合、既に読み込まれ、JIT でコンパイルされ、最適化されているコードが含まれることがあります。 **モジュールの読み込みに抑制する状況の JIT 最適化を**オプションも何も起こりませんようなコードが、アタッチした後に読み込まれるモジュールに影響します。 さらに、**モジュールの読み込みに抑制する状況の JIT 最適化を**オプションでは NGEN で作成された WinForms.dll などのモジュールには影響しません。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)   
 [実行中のプロセスをアタッチします。](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [マネージ実行プロセス](/dotnet/standard/managed-execution-process)