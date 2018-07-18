---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, 難読化, .NET, 無料, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio 2017 に含まれる無料の Dotfuscator Community Edition を使用して .NET アプリケーションを保護する方法について説明します。
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: c34eec9f8eab1f870344ec6995bfcbd8fea8739c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704397"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection - Dotfuscator* は、安全なソフトウェア開発ライフサイクルに容易に適合する、包括的な .NET アプリケーションの保護機能を提供します。
この機能により、デスクトップ、モバイル、サーバー、組み込みのアプリケーションを強化および保護し、余分なものを取り除くことで、企業秘密やその他の知的財産 (IP) を守り、違法コピーや偽造を減らし、改ざんと権限のないデバッグを防止できます。
Dotfuscator はコンパイル済みのアセンブリで動作し、追加のプログラミングやソース コードへのアクセスは不要です。

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>保護が必要な理由

**知的財産 (IP) を保護**することは重要です。
アプリケーションのコードに含まれる設計と実装の詳細は、IP であるとみなすことができます。
ただし、.NET Framework で構築されたアプリケーションには[重要なメタデータと高度な中間コードが含まれており][assemblies]、多数存在する無料の自動化ツールのいずれかを使用するだけで、簡単にリバース エンジニアリングを実行できます。
リバース エンジニアリングを中断および停止させることで、許可されていない IP の漏えいを防止できるだけでなく、コードに企業秘密が含まれていることを示すことができます。
Dotfuscator は、元のアプリケーションの動作を維持しながら、.NET アセンブリを[難読化][obfuscation]し、リバース エンジニアリングを防止します。

**アプリケーションの整合性を保護**することも重要です。
リバース エンジニアリングだけでなく、犯罪者がアプリケーションの違法コピーを作成したり、実行時のアプリケーションの動作を変更したり、データを操作したりしようとすることもあります。
Dotfuscator は、改ざん、サード パーティによるデバッグ、ルート化されたデバイスを含め、[許可のない使用を検出、報告し、それに対応する][checks]機能をアプリケーションに注入します。

保護されたソフトウェア開発ライフサイクルに Dotfuscator が適合するしくみの詳細については、PreEmptive Solution の「[SDL App Protection (SDL アプリの保護)][sdl-protection]」のページを参照してください。

## <a name="about-dotfuscator-ce"></a>Dotfuscator CE について

Microsoft Visual Studio 2017 のコピーには、Dotfuscator CE としても知られる ***PreEmptive Protection - Dotfuscator* Community Edition** の無料ライセンスが含まれています。
Visual Studio 2017 に含まれている Dotfuscator CE のバージョンをインストールする方法の手順については、[インストールに関するページ][install]を参照してください。

Dotfuscator CE は、広範な[ソフトウェアの保護と強化][software-protection]のサービスを開発者、アーキテクト、およびテスト担当者に提供します。
[.NET の難読化][obfuscation]および Dotfuscator CE に含まれるその他の[アプリケーションの保護][app-protection]機能の例を以下に挙げます。

* 識別子の*[名前の変更][renaming]* により、コンパイル済みアセンブリのリバース エンジニアリングをさらに難しくします。
* *[改ざん防止][tamper]* 機能により、改ざんされたアプリケーションの実行を検出し、インシデント アラートを送信して、改ざんされたセッションを終了します。
* *[デバッグ防止][debug]* 機能により、実行中のアプリケーションに対するデバッガーの添付ファイルを検出し、インシデント アラートを送信して、デバッグ セッションを終了します。
* *[ルート化されたデバイスの防止][root]* 機能により、ルート化された Android デバイスで実行されているアプリケーションを検出し、そのデバイスでのセッションを終了します。
* *[アプリケーションの有効期限の動作][shelflife]* は、"有効期限" の日付をエンコードし、有効期限の後にアプリケーションが実行された際にアラートを送信し、期限切れのアプリケーション セッションを終了します。
* *[例外の追跡][exceptions]* は、アプリケーション内で発生する未処理の例外を監視します。
* *[セッション][sessions]および[機能][features]の使用追跡*は、実行されたアプリケーション、それらのアプリケーションのバージョン、および実行された機能を特定します。

お客様のアプリケーション保護戦略にどのように適合するかを含めた、これらの機能の詳細については、[機能に関するページ][capabilities]を参照してください。

Dotfuscator CE には、すぐに利用できる基本的な保護機能が用意されています。
Dotfuscator CE の登録済みのユーザー、*PreEmptive Protection - Dotfuscator* Professional Edition のユーザー、および世界トップレベルの [.NET Obfuscator][net-obfuscator] のユーザーは、さらに多くのアプリケーションの保護対策を利用できます。
Dotfuscator の拡張方法については、[アップグレードに関するページ][upgrades]を参照してください。

## <a name="getting-started"></a>作業の開始

Visual Studio から Dotfuscator CE の使用を開始するには、**クイック起動** (Ctrl + Q) 検索バーに `dotfuscator` と入力します。

* Dotfuscator CE が既にインストールされている場合は、**クイック起動**によって、Dotfuscator CE ユーザー インターフェイスを起動する *[メニュー]* オプションが表示されます。 詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。
* Dotfuscator CE がまだインストールされていない場合は、 **クイック起動**によって、関連する *[インストール]* オプションが表示されます。 詳細については、[インストールに関するページ][install]を参照してください。

**最新バージョン**の Dotfuscator CE も、[preemptive.com の Dotfuscator Downloads ページ][download]からダウンロードできます。

## <a name="full-documentation"></a>すべてのドキュメント

このページとそのサブページでは、Dotfuscator CE 機能の概略に加え、[ツールをインストールする方法][install]について説明しています。

[Dotfuscator CE ユーザー インターフェイスの使用を開始する方法][get-started]を含めた、詳細な使用方法の説明については、[Dotfuscator CE の完全なユーザー ガイド (preemptive.com)][full] を参照してください。

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[exceptions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
[sessions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
[features]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html