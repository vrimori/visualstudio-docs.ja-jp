---
title: 例外の後に実行を継続 |Microsoft ドキュメント
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ebdb034c85bce6924c90467e0f3cda3bb765832
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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