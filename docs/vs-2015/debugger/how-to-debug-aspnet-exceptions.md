---
title: '方法: ASP.NET の例外のデバッグ |Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d505e67018c24f659e88401b565011a4c7bea96
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789214"
---
# <a name="how-to-debug-aspnet-exceptions"></a>方法 : ASP.NET の例外をデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

例外のデバッグは、堅牢な開発の重要な部分[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]アプリケーション。 例外をデバッグする方法についての全般については、「[デバッガーでの例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)します。  
  
 未処理のデバッグに[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]例外、行う必要がありますにデバッガーを中断することを確認します。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ランタイムにはトップレベルの例外ハンドラーがあります。 そのため、デバッガーは既定では、ハンドルされない例外で実行を中断することはありません。 例外がスローされたときに、デバッガーに割り込むを選択する必要があります**例外は、ときに中断: スロー**でその特定の例外の設定、**例外** ダイアログ ボックス。  
  
 マイ コードのみを有効にした場合**例外は、ときに中断: スロー**デバッガーが .NET Framework メソッドやその他のシステム コードで例外がスローされた場合、すぐに中断は発生しません。 デバッガーがシステム コード以外のコードをヒットするまで実行は継続され、ヒットした時点でデバッガーは中断されます。 つまり、例外が発生したときにシステム コードをステップ実行する必要はありません。  
  
 マイ コードのみでは、さらに活用できるもう 1 つのオプション:**例外は、ときに中断: user-unhandled**します。 例外にこの設定を選択すると、ユーザー コードで例外が取得され、処理された場合にのみ、デバッガーによってユーザー コードの実行が中断されます。 この設定では、トップレベルの [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 例外ハンドラーの効果が無視されます。この例外ハンドラーがユーザー コードではないためです。  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>[マイ コードのみ] で ASP.NET 例外を有効にするには  
  
1.  **デバッグ** メニューのをクリックして**例外**します。  
  
     **例外** ダイアログ ボックスが表示されます。  
  
2.  **Common Language Runtime Exceptions**行で、**スロー**または**user-unhandled**します。  
  
     使用する、 **user-unhandled**設定、**マイ コードのみ**有効にする必要があります.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>ASP.NET の例外処理で推奨される手順を使用するには  
  
-   予測でき、処理方法がわかる例外をスローできるコードを、`try … catch` ブロックで囲みます。 たとえば場合は、アプリケーションは、XML Web サービスまたは SQL Server に直接呼び出しを行うは、そのコードがでなければなりません**try… catch**数多くの例外が発生する可能性があるためにをブロックします。



