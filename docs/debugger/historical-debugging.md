---
title: デバッグ履歴 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc16c6e6186d53bd08bd0634e07a4d1172859280
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54227253"
---
# <a name="historical-debugging-c-visual-basic-c"></a>デバッグ履歴 (C#、Visual Basic、C++)

デバッグ履歴は、IntelliTrace で収集された情報に依存するデバッグのモードです。 アプリケーションの実行内を前後に移動して、実行の状態を調べることができます。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
## <a name="why-use-historical-debugging"></a>デバッグ履歴を使用する理由

 ブレークポイントを設定してバグを探すのは、どちらかというと行き当たりばったりな方法です。 バグがありそうな場所のコードの近くにブレークポイントを設定し、デバッガーでアプリケーションを実行して、ブレークポイントがヒットし、実行が中断した場所でバグの原因が明らかになることを期待します。 原因がわからない場合は、コードの別の場所にブレークポイントを設定し、デバッガーを再実行して、問題が見つかるまで繰り返しテスト手順を行う必要があります。  
  
 ![ブレークポイントを設定する](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 IntelliTrace とデバッグ履歴を使用すると、アプリケーション内を移動して状態を調べることができ (呼び出し履歴およびローカル変数)、ブレークポイントを設定し、デバッグを再実行し、テスト手順を繰り返す必要はありません。 これにより多くの時間を節約できます。実行に時間がかかるテスト シナリオの深い場所にバグがある場合は特に有効です。  
  
## <a name="how-do-i-start-using-historical-debugging"></a>デバッグ履歴の使用を始める方法

 IntelliTrace は既定で有効になります。 行う必要があるすべてが対象のイベントと関数の呼び出しは、関心のあるし、の完全なアプリケーション状態のスナップショットを表示するかどうかを決定します。 調べる対象の定義について詳しくは、「[IntelliTrace の機能](../debugger/intellitrace-features.md)」をご覧ください。 言語アプリによってサポートされている機能は変化の種類。

 - デバッグ履歴のスナップショットを表示するを参照してください[IntelliTrace を使用して前のアプリ状態を調べる。](../debugger/view-historical-application-state.md)
 - 変数を検査して、コードを移動する方法については、次を参照してください[デバッグ履歴を使用してアプリを調べる。](../debugger/historical-debugging-inspect-app.md)
 - IntelliTrace イベントでのデバッグの詳細については、次を参照してください。[チュートリアル: IntelliTrace を使用した](../debugger/walkthrough-using-intellitrace.md)します。