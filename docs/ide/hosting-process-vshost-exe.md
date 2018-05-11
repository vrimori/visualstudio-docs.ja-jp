---
title: ホスト プロセス (vshost.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bba0463870f4d615e45d8f2c11071bfd8a1b8009
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="hosting-process-vshostexe"></a>ホスト プロセス (vshost.exe)

Visual Studio のホスト プロセスは、デバッグのパフォーマンスを向上させ、部分信頼のデバッグを可能にし、デザイン時に式を評価できるようにする機能です。 ホスト プロセスのファイルは、ファイル名に *vshost* が含まれ、プロジェクトの出力フォルダーに配置されます。 詳細については、「[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)」をご覧ください。

> [!NOTE]
> ホスト プロセスのファイル (*.vshost.exe*) は、Visual Studio によって使われるものなので、直接実行したり、アプリケーションと共に配置したりしないでください。

## <a name="improved-debugging-performance"></a>デバッグ パフォーマンスの向上
 ホスト プロセスは、アプリケーション ドメインを作成し、デバッガーをアプリケーションに関連付けます。 これらのタスクを実行すると、デバッグが開始されてからアプリケーションが実行を始めるまでに、大きな遅延が発生する可能性があります。 ホスト プロセスは、アプリケーション ドメインの作成とデバッガーの関連付けをバックグラウンドで行い、アプリケーションの実行と実行の間でアプリケーション ドメインとデバッガーの状態を保存することにより、パフォーマンスを向上させます。 アプリケーション ドメインの詳細については、「[アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)」をご覧ください。

## <a name="partial-trust-debugging"></a>部分信頼のデバッグ
 **プロジェクト デザイナー**の [[セキュリティ] ページ](../ide/reference/security-page-project-designer.md)では、アプリケーションを部分信頼アプリケーションとして指定することができます。 部分信頼アプリケーションをデバッグするには、アプリケーション ドメインの特別な初期化が必要です。 ホスト プロセスは、この初期化を処理します。

## <a name="design-time-expression-evaluation"></a>デザイン時の式評価
 デザイン時の式評価を使うと、**[イミディエイト]** ウィンドウからコードをテストすることができ、アプリケーションを実行する必要がありません。 ホスト プロセスは、デザイン時の式評価の間にこのコードを実行します。 詳細については、「[イミディエイト ウィンドウ](../ide/reference/immediate-window.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)
- [方法: ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)
- [イミディエイト ウィンドウ](../ide/reference/immediate-window.md)
- [アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)