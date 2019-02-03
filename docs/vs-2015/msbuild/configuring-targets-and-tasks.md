---
title: ターゲットとタスクを構成する | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 304ebde1c30a78ab000a1fae4a16b5082b0aeecf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769267"
---
# <a name="configuring-targets-and-tasks"></a>ターゲットとタスクの構成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild のターゲットとタスクを、MSBuild のアウトプロセスで実行するように構成できます。これにより、開発時に実行しているコンテキストとは異なるコンテキストを対象とすることができます。 たとえば、開発用コンピューターが 64 ビットの .NET Framework 4.5 オペレーティング システムで動作している場合でも、32 ビットの .NET Framework 2.0 アプリケーションを対象とすることができます。 .NET Framework 4 以前で動作するコンピューターを対象にすることもできます。 32 ビットまたは 64 ビットのビット プロセスと特定の .NET Framework のバージョンの組み合わせは、*ターゲット コンテキスト*と呼ばれます。  
  
## <a name="installation"></a>インストール  
 .NET Framework 4.5 と 4.5.1 では、.NET Framework 4 の共通言語ランタイム (CLR)、ターゲット、タスク、およびツールが置き換わりますが、名前は変更されません。 .NET Framework 4.5.1 は [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] の一部としてインストールされます。  
  
 MSBuild を Visual Studio とは別にインストールする場合は、[MSBuild ダウンロード](http://go.microsoft.com/fwlink/?LinkId=309745)からインストール パッケージをダウンロードします。 また、使用する .NET Framework のバージョンもインストールする必要があります。  
  
## <a name="targets-and-tasks"></a>ターゲットとタスク  
 MSBuild では、より大きいセットのコンテキストを対象とするために、特定のビルド タスクをアウトプロセスで実行できます。  たとえば、32 ビットの MSBuild が、64 ビット コンピューターを対象とするために、64 ビット プロセスでビルド タスクを実行する場合があります。 これは `UsingTask` 引数と `Task` パラメーターによって制御されます。 .NET Framework 4.5 でインストールされたターゲットによって、これらの引数とパラメーターが設定されます。さまざまなターゲット コンテキスト用のアプリケーションをビルドする際に、これらの引数やパラメーターを変更する必要はありません。  
  
 独自のターゲット コンテキストを作成する場合は、これらの引数とパラメーターを適切に設定する必要があります。 サンプルについては、.NET Framework 4.5 の Microsoft.Common.targets ファイルおよび Microsoft.Common.Tasks ファイルを参照してください。  複数のターゲット コンテキストで動作するカスタム タスクの作成方法、および既存のタスクの変更方法については、「[方法 : ターゲットとタスクを構成する](../msbuild/how-to-configure-targets-and-tasks.md)」を参照してください。  
  
## <a name="see-also"></a>「  
 [マルチ ターゲット](../msbuild/msbuild-multitargeting-overview.md)
