---
title: ホスティング プロセスのデバッグと |Microsoft Docs
ms.custom: ''
ms.date: 08/01/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 59ef28f5724c12fd9897adbaa9125bafe26beb60
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468261"
---
# <a name="debugging-and-the-hosting-process"></a>プロセスのデバッグとホスト
Visual Studio のホスト プロセスでは、デバッガーのパフォーマンスを向上させ、部分信頼のデバッグやデザイン時の式の評価など、新しいデバッガー機能が使用できるようになりました。 必要に応じてホスト プロセスを無効にすることもできます。 次のセクションでは、ホスト プロセスがある場合とない場合のデバッグの違いについて説明します。

> [!NOTE]
> Visual Studio 2017 では、ホスト プロセスを使用してデバッグするためのオプションは不要になったし、が削除されました。 詳細については、次を参照してください。[デバッグ: Visual Studio 2017 の目的に速度を最低お気に入り職種](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)します。

## <a name="partial-trust-debugging-and-click-once-security"></a>部分信頼のデバッグと ClickOnce のセキュリティ
 部分信頼のデバッグにはホスト プロセスが必要です。 ホスト プロセスを無効にすると、 **[プロジェクトのプロパティ]** の **[セキュリティ]** ページで部分信頼が有効になっている場合でも、部分信頼のデバッグは機能しません。 詳細については、次を参照してください。[方法: 部分信頼アプリケーションをデバッグ](../debugger/how-to-debug-a-partial-trust-application.md)します。

## <a name="design-time-expression-evaluation"></a>デザイン時の式評価
 デザイン時の式では、常にホスト プロセスが使用されます。 **[プロジェクトのプロパティ]** でホスト プロセスを無効にすると、クラス ライブラリ プロジェクトでデザイン時の式の評価も無効になります。 他のプロジェクトの種類では、デザイン時の式の評価は無効になりません。 代わりに、Visual Studio で実際の実行可能ファイルが起動され、ホスト プロセスを使用せずにデザイン時の評価に使用されます。 この違いがあるため、結果も異なる可能性があります。

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName の違い
 `AppDomain.CurrentDomain.FriendlyName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `AppDomain.CurrentDomain.FriendlyName` を呼び出すと、 *app_name*`.vhost.exe`が返されます。 ホスト プロセスを無効にして呼び出した場合は、 *app_name*`.exe`が返されます。

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName の違い
 `Assembly.GetCallingAssembly().FullName` は、ホスト プロセスが有効かどうかによって異なる結果を返します。 ホスト プロセスを有効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、 `mscorlib`が返されます。 ホスト プロセスを無効にして `Assembly.GetCallingAssembly().FullName` を呼び出すと、アプリケーション名が返されます。

## <a name="see-also"></a>関連項目

- [方法 : 部分信頼アプリケーションをデバッグする](../debugger/how-to-debug-a-partial-trust-application.md)