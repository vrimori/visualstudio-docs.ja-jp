---
title: '方法: ASP.NET の例外のデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 5923818e93170ded1f857ac20d42cd6134aed5d3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-aspnet-exceptions"></a>方法 : ASP.NET の例外をデバッグする
例外のデバッグは、堅牢な開発の重要な部分[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリケーションです。 例外をデバッグする方法に関する一般情報が、[デバッガーでは、例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)です。  
  
 未処理のデバッグに[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]の例外を除き、する必要がありますにデバッガーを中断することを確認します。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ランタイムにはトップレベルの例外ハンドラーがあります。 そのため、デバッガーは既定では、ハンドルされない例外で実行を中断することはありません。 選択に例外がスローされたときに、デバッガーを分割する必要があります**例外は、するときに中断する: スロー**でその特定の例外の設定、**例外** ダイアログ ボックス。  
  
 マイ コードのみを有効にした場合**例外は、するときに中断する: スロー**デバッガーが .NET Framework メソッドやその他のシステム コードで例外がスローされた場合、すぐに中断は発生しません。 デバッガーがシステム コード以外のコードをヒットするまで実行は継続され、ヒットした時点でデバッガーは中断されます。 つまり、例外が発生したときにシステム コードをステップ実行する必要はありません。  
  
 マイ コードのみでは、さらに便利なことができる別のオプション:**例外は、するときに中断する: ユーザーに処理されない**です。 例外にこの設定を選択すると、ユーザー コードで例外が取得され、処理された場合にのみ、デバッガーによってユーザー コードの実行が中断されます。 この設定では、トップレベルの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外ハンドラーの効果が無視されます。この例外ハンドラーがユーザー コードではないためです。  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>[マイ コードのみ] で ASP.NET 例外を有効にするには  
  
1.  **デバッグ** メニューのをクリックして**例外**です。  
  
     **例外** ダイアログ ボックスが表示されます。  
  
2.  **Common Language Runtime Exceptions**行で、**スロー**または**ユーザーよって処理されない**です。  
  
     使用する、**ユーザーよって処理されない**設定、**マイ コードのみ**有効にする必要があります.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>ASP.NET の例外処理で推奨される手順を使用するには  
  
-   予測でき、処理方法がわかる例外をスローできるコードを、`try ... catch` ブロックで囲みます。 たとえば場合は、アプリケーションの呼び出しを行う XML Web サービスまたは SQL Server に直接、そのコードがでなければなりません**try… catch**数多くの例外が発生する可能性があるためにをブロックします。

## <a name="see-also"></a>関連項目
[ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)