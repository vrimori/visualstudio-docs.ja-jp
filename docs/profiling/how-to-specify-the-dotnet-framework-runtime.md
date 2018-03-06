---
title: "方法: .NET Framework ランタイムを指定する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: a060315c17dfc351aaa3cba5fec52fdcfc3f9b0c
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-the-net-framework-runtime"></a>方法: .NET Framework ランタイムを指定する

リリース [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] では、アプリケーションは [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ランタイムのさまざまなバージョンを使用してビルドされたモジュールで構成できます。 既定では、Visual Studio プロファイリング ツールは、アプリケーションによって読み込まれる最初のランタイムをプロファイリングします。 プロファイラーを使用してアプリケーションを開始するときと、既に実行中のアプリケーションにプロファイラーをアタッチするときにランタイムがプロファイリングするよう指定できます。

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>プロファイラーを使用したアプリケーションの開始時にプロファイリングする .NET Framework ランタイムを指定するには

1. **パフォーマンス エクスプローラー**で、パフォーマンス セッション名を右クリックして **[プロパティ]** をクリックしてから、**[詳細]** をクリックします。

     **[ターゲット CLR バージョン]** 一覧ボックスに **[自動]** およびコンピューターにインストールされている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ランタイムのバージョンが表示されます。

2. 次のいずれかの操作を実行します。

    - プロファイリングする CLR のバージョンをクリックします。

    - **[自動]** をクリックして、アプリケーションが最初に読み込んだバージョンをプロファイルします。

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>アプリケーションにプロファイラーをアタッチするときにプロファイリングする .NET Framework ランタイムを指定するには

1. [分析] メニューの [プロファイラー] をポイントし、[アタッチ/デタッチ] をクリックします。

2. [プロファイラーのプロセスへのアタッチ] ダイアログ ボックスで、プロファイリングするプロセスをクリックします。

     **[ターゲット CLR バージョン]** 一覧ボックスに **[自動]** およびコンピューターにインストールされている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ランタイムのバージョンが表示されます。

3. 次のいずれかの操作を実行します。

    - プロファイリングする CLR のバージョンをクリックします。

    - **[自動]** をクリックして、プロファイラーがアプリケーションにアタッチされたときに読み込まれたバージョンをプロファイリングします。