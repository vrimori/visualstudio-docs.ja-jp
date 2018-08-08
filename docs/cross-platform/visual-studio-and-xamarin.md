---
title: Visual Studio と Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: ef599a67dcb81586bd31fd08836c0a95b812bde1
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251228"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio と Xamarin

Xamarin はネイティブの iOS、Android、Windows のアプリを一般的な C#/.NET コード ベースから構築するためのモバイル アプリ開発プラットフォームです。 Xamarin で記述されたアプリでは、プラットフォーム間で 75% ～ほぼ 100% のコードを再利用できます。 また、基になるプラットフォーム API に完全アクセスし、ネイティブ ユーザー インターフェイスを組み込むことができます。 実行時のパフォーマンスに与える影響を最小限に抑え、プラットフォーム固有のパッケージにコンパイルされます。 (注: Xamarin は F# もサポートしていますが、このドキュメントでは C# のみを扱います。 Visual Basic は現時点ではサポートされていません。)

C#、.NET、Visual Studio に親しんだ開発者であれば、モバイル アプリを Xamarin で開発するとき、同じような機能や生産性を享受できます。 たとえば、Objective-C や Java のようなネイティブ コーディング言語を学習しなくても、Android、iOS、Windows デバイスでリモート デバッグできます。 これは驚くことではありません。NASCAR、Aviva や MixRadio のような、素晴らしいユーザー インターフェイスを持つ高性能なアプリの多くは、Xamarin を使用して作成されているからです。

このドキュメントでは、以下の項目を通して **Xamarin を使用した Visual Studio** のすべての機能を評価できます。

-   最初に、時間のかかるプロセスである、 [Setup and install](../cross-platform/setup-and-install.md)を行います (インターネット接続の速度、既にインストールしているものや選択するオプションによって異なりますが、通常 2 ～ 4 時間)。

-   インストーラーが実行している間、「[Xamarin によるモバイル開発の概要](learn-about-mobile-development-with-xamarin.md)」を確認し、Xamarin の性質や Xamarin.Forms とネイティブ UI との比較などを理解しましょう。

-   インストールが完了したら、[Xamarin 環境を検証する](../cross-platform/verify-your-xamarin-environment.md)作業を実行します。

-   チュートリアル「[Visual Studio での Xamarin Froms を使用したアプリ作成の基本事項](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)」を確認して、作業を仕上げます。

[任意のエディションの Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community、Professional、Enterprise) で、Xamarin のすべての機能を使用できます。 別個のライセンスは必要ありません。

> [!NOTE]
>  これらの手順では、Windows や Visual Studio での開発経験がある開発者のために、コンピューターの最も簡単で単純な構成方法について説明します。 この構成を使用すると、Mac と対話するだけで iOS シミュレーターとテザリングされたデバイスを使用できるので、開発作業全体が簡略化されます。 Mac に慣れている場合には、Parallels または VMWare 内の Visual Studio を実行するか、Visual Studio for Mac を使用することをお勧めします。 詳細については、「[Setup, install, and verifications for Mac users](../cross-platform/setup-install-and-verifications-for-mac-users.md)」(Mac ユーザー向けのセットアップ、インストール、および 検証) をご覧ください。

> [!NOTE]
>  HTML および CSS ベースでのクロスプラットフォーム開発ソリューションをお探しの場合は、[Visual Studio でのクロスプラットフォーム開発](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML)に関するページで説明されている Visual Studio Tools for Apache Cordova をご確認ください。