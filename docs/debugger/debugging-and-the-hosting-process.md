---
title: ホスト プロセスのデバッグと |Microsoft ドキュメント
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
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb7564ca501817977b68cefc84ddeba1cd55a939
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-and-the-hosting-process"></a>プロセスのデバッグとホスト
Visual Studio のホスト プロセスでは、デバッガーのパフォーマンスを向上させ、部分信頼のデバッグやデザイン時の式の評価など、新しいデバッガー機能が使用できるようになりました。 必要に応じてホスト プロセスを無効にすることもできます。 詳細については、「 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md)」を参照してください。 次のセクションでは、ホスト プロセスがある場合とない場合のデバッグの違いについて説明します。  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>部分信頼のデバッグと ClickOnce のセキュリティ  
 部分信頼のデバッグにはホスト プロセスが必要です。 ホスト プロセスを無効にすると、 **[プロジェクトのプロパティ]** の **[セキュリティ]**ページで部分信頼が有効になっている場合でも、部分信頼のデバッグは機能しません。 詳細については、次のトピックを参照してください。 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) および [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>デザイン時の式評価  
 デザイン時の式では、常にホスト プロセスが使用されます。 **[プロジェクトのプロパティ]** でホスト プロセスを無効にすると、クラス ライブラリ プロジェクトでデザイン時の式の評価も無効になります。 他のプロジェクトの種類では、デザイン時の式の評価は無効になりません。 代わりに、Visual Studio で実際の実行可能ファイルが起動され、ホスト プロセスを使用せずにデザイン時の評価に使用されます。 この違いがあるため、結果も異なる可能性があります。  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName の違い  
 `AppDomain.CurrentDomain.FriendlyName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `AppDomain.CurrentDomain.FriendlyName` を呼び出すと、 *app_name*`.vhost.exe`が返されます。 ホスト プロセスを無効にして呼び出した場合は、 *app_name*`.exe`が返されます。  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName の違い  
 `Assembly.GetCallingAssembly().FullName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、 `mscorlib`が返されます。 ホスト プロセスを無効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、アプリケーション名が返されます。  
  
## <a name="see-also"></a>関連項目  
 [ホスト プロセス (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [方法: 部分信頼アプリケーションのデバッグ](../debugger/how-to-debug-a-partial-trust-application.md)   
 [方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)