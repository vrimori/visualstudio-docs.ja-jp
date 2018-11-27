---
title: 例外の後に実行を継続 |Microsoft Docs
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
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 947a17993fe0e8366149d1cef79c26c68b11d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730031"
---
# <a name="continuing-execution-after-an-exception"></a>例外後の実行の継続
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

例外が発生してデバッガーによる実行が中断されると、ダイアログ ボックスが表示されます。 Visual Basic または c#、について表示されます、[例外処理アシスタント](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) ダイアログ ボックスで、既定では。 C++ の場合、古いわかります**例外** ダイアログ ボックス。 Visual Basic または c# を使用しているが、無効にしているかどうか、**例外処理アシスタント**で、**オプション** ダイアログ ボックスが表示されます、**例外** ダイアログ ボックス。  
  
 ときに、**例外処理アシスタント**または**例外** ダイアログ ボックスが表示されたら、例外の原因となった問題を解決しようとすることができます。  
  
## <a name="managed-code"></a>マネージド コード  
 マネージド コードでは、未処理の例外の後に同じスレッドで実行を継続できます。 **例外処理アシスタント**例外がスローされたポイントにコール スタックをアンワインドします。  
  
## <a name="native-code"></a>ネイティブ コード  
 ネイティブ C/C++ では、2 つのオプションがあります。  
  
-   クリックすることができます**中断**問題を解決しようとします。 中断モードでは、内のフレームを右クリックして、コール スタックをアンワインドできます、**呼び出し履歴**ウィンドウと選択**このフレームにアンワインド**ショートカット メニューの します。 、デバッグを続行するときに、**例外**、問題が解決しない場合に、ダイアログ ボックスが再度表示されます。 それ以外の場合、**例外** ダイアログ ボックスは表示されません。  
  
-   クリックすることができます**続行**問題を解決しようとしないで実行を続行します。 **例外** ダイアログ ボックスが表示されます。  
  
## <a name="mixed-code"></a>混合コード  
 ネイティブ コードとマネージド コードが混在するコードをデバッグしているときに、ハンドルされていない例外が発生した場合、オペレーティング システムの制約により、呼び出し履歴のアンワインドが抑制されます。 ショートカット メニューを使用して呼び出し履歴をさかのぼろうとすると、混合コードのデバッグ中は、ハンドルされていない例外からアンワインドすることはできないという内容のエラー メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)





