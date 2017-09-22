---
title: "Visual Studio の回復不能なプロセス エラー | Microsoft Docs"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 2263956f-3ae0-4bdc-9d3a-4991dfaf4ddb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: b5f39ea962f6b4dcc0e2c6947b2eeabf53d3329a
ms.openlocfilehash: ba0a0aacc68e2eb9a5cd9b5b672808a71e8c09eb
ms.contentlocale: ja-jp
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio の回復不能なプロセス エラー

Visual Studio 2017 では、アウト プロセスのプロセスをいくつか利用し、ライブ単体テストやコード アナライザーなど、必要なバックグラウンド タスクを実行します。 このようなプロセスはアウト プロセスで実行され、Visual Studio のパフォーマンスを改善します。たとえば、リソースを集中的に使用するジョブを長時間実行するとき、Visual Studio の応答が速くなります。 また、Visual Studio は 32 ビット プロセスのため、プロセスをアウト プロセスで実行すると、メモリを集中的に使用する作業にたくさんのメモリ領域が与えられます。

このようなプロセスのいずれかが何らかの理由で終了すると、ポップアップ情報バーが現れ、次のメッセージが表示されます。

"Unfortunately, a process used by Visual Studio has encountered an unrecoverable error. We recommend saving your work, and then closing and restarting Visual Studio. (申し訳ございませんが、Visual Studio で使用されているプロセスに回復できないエラーが発生しました。作業を保存し、Visual Studio を再起動することを推奨します。)"

このメッセージが表示されたら、すぐに作業を保存し、Visual Studio を閉じ、再起動してください。 そうしないと、すぐに Visual Studio がクラッシュする可能性があります。

## <a name="list-of-processes"></a>プロセスの一覧

次は、Visual Studio で使用されるアウト プロセス プロセスの一覧です。Visual Studio が適切に動作するために実行する必要があります。

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

