---
title: "例外の後に実行を継続 |Microsoft ドキュメント"
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
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9491eb19796c766d216af458ca122b1fa5032596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="continuing-execution-after-an-exception"></a>例外後の実行の継続
デバッガーは、例外のため実行を中断と、表示されます、**例外ヘルパー**既定でします。 無効にした場合、**例外ヘルパー**で、**オプション** ダイアログ ボックスが表示されます、**例外処理アシスタント**(c# または Visual Basic) または**例外**  ダイアログ ボックス (C++)。  
  
 ときに、**例外ヘルパー**が表示されたら、例外の原因となった問題を解決しようとすることができます。
  
## <a name="managed-and-native-code"></a>マネージ コードとネイティブ コード  
 、マネージとネイティブ コードでハンドルされない例外の後に同じスレッドで実行を継続することができます。 **例外ヘルパー**例外がスローされた時点に呼び出し履歴をアンワインドします。
  
## <a name="mixed-code"></a>混合コード  
 ネイティブ コードとマネージ コードが混在するコードをデバッグしているときに、ハンドルされていない例外が発生した場合、オペレーティング システムの制約により、呼び出し履歴のアンワインドが抑制されます。 ショートカット メニューを使用して呼び出し履歴をさかのぼろうとすると、混合コードのデバッグ中は、ハンドルされていない例外からアンワインドすることはできないという内容のエラー メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)