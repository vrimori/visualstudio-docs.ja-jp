---
title: "Visual Studio 2017 SDK の新機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 3da360fc4df5516f5d976f807319c07b49d8c4e8
ms.contentlocale: ja-jp
ms.lasthandoff: 03/07/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK の新機能します。

Visual Studio SDK では、Visual Studio 2017 の次の新規および更新の機能があります。

## <a name="vsix-v3-format"></a>VSIX v3 形式

Visual Studio 2017 の新しい軽量のインストールをサポートするためには、VSIX 拡張機能マニフェスト形式がバージョン 3 (VSIX v3) に更新されました。

新しい形式には、サポートがあります。

* 検出され、VSIXInstaller によってインストールの前提条件が明示的に宣言します。
* 拡張機能のインストールで Ngen'ing アセンブリ。
* 通常の拡張機能のルート以外の資産をインストールしています。

これらの変更の詳細については、次のトピックを参照してください。

* [2017 の拡張機能への変更](breaking-changes-2017.md)
* [VSIX v3 での Ngen のサポート](ngen-support.md)
* [拡張機能フォルダー外でのインストール](set-install-root.md)
* [よく寄せられる質問の Visual Studio 2017 機能拡張](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Visual Studio 2017 への移行の機能拡張プロジェクト

Visual Studio 2017 を機能拡張プロジェクトおよびその VSIX マニフェストを更新する方法については、次を参照してください。[方法: Visual Studio 2017 を機能拡張プロジェクトの移行](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)します。

## <a name="lightweight-solution-load-lsl"></a>軽量なソリューションの読み込み (LSL)

軽量なソリューションの読み込みとは、ソリューションの読み込み時間を大幅に減少するより迅速に生産性を向上させることが可能 VS 2017 の新機能です。 LSL を有効にすると、Visual Studio は完全に読み込まれませんプロジェクトで作業を開始するまで。

Visual Studio 拡張機能は LSL の影響を与える可能性があります。 機能が完全に読み込まれるプロジェクトに依存する拡張機能の動作または正常に動作しない可能性がありますできません。 参照してください[ライトウェイト ソリューションの読み込み](lightweight-solution-load-extension-impact.md)拡張機能が受ける可能性がありますおよび拡張機能を更新する方法のガイダンスが用意されているかどうかを確認します。

## <a name="custom-project-and-item-templates"></a>カスタムのプロジェクトおよび項目テンプレート

Visual Studio 2017 以降、カスタムのプロジェクトおよび項目テンプレートのスキャンが不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するマニフェスト ファイルのテンプレートを提供する必要があります。 Visual Studio 2017 を使用して、VSIX 拡張を更新できます。 MSI を使用して、拡張機能を展開する場合は、テンプレートのマニフェスト ファイルを手動で生成する必要があります。 詳細については、次を参照してください。[をアップグレードするカスタムのプロジェクトおよび項目テンプレートを Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)します。 テンプレートのマニフェスト スキーマの詳細は「 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)します。

## <a name="updated-extension-performance-guidelines"></a>更新された拡張機能のパフォーマンスに関するガイドライン

新しい[方法: 拡張機能のパフォーマンスの診断](how-to-diagnose-extension-performance.md)トピックの「[管理 VSPackages](managing-vspackages.md)を検出して、Visual Studio 拡張機能への影響を分析する方法を表示する起動とソリューション、読み込み時間。

