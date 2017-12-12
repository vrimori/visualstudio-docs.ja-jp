---
title: "Dotfuscator Community Edition (CE) をアップグレードする | Microsoft Docs"
ms.date: 2017-02-08
ms.devlang: dotnet
ms.technology: vs-ide-general
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, 難読化, .NET, 無料, Visual Studio 2017, アップグレード, コマンド ライン"
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: "Visual Studio 2017 に含まれる無料の Dotfuscator Community Edition をアップグレードする方法について説明します。"
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
manager: ghogen
ms.openlocfilehash: 261fc98312914f5a80d2302a90e360dfde2ca17f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE) をアップグレードする

Dotfuscator Community Edition (Dotfuscator CE) には、Microsoft Visual Studio.を使用しているすべての開発者がすぐに利用できる多くのアプリケーション保護機能と強化機能がありますが、
Dotfuscator のバージョンをアップグレードすると、さらに多くの機能を利用できるようになります。

## <a name="registering-dotfuscator-ce"></a>Dotfuscator CE の登録

Dotfuscator CE の登録ユーザーは、[コマンド ライン サポート][cli]などの追加機能にアクセスできます。コマンド ラインを使用すると、Dotfuscator CE を自動ビルド プロセスに簡単に統合できます。
また、登録することで、[難読化されたスタック トレースをデコードする][decode-obfuscated]ために使用される組み込みツールである Lucidator へのアクセスが許可されます。

登録は無料で、簡単な手順ですぐに実行できます。
Dotfuscator CE を登録する方法については、[「Dotfuscator CE User Guide」(Dotfuscator CE ユーザー ガイド) の「Registering Dotfuscator CE」(Dotfuscator CE の登録) セクション][register-ce]を参照してください。

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community Edition には基本的なレベルの保護機能である **_PreEmptive Protection - Dotfuscator_ が備わっています。一方、Professional Edition** では、難読化変換機能と保護機能が強化されています。
次の設定があります。

* *知的財産の保護*
  * Enhanced Overload Induction™、ランダムな識別子選択など、追加の名前変更オプション。
  * 難読化されたスタック トレースをデコードするツール。
  * エンタープライズレベルの難読化変換へのアクセス ([自動コード逆コンパイルを阻止する目的の変換など][control-flow])。
  * [機密性の高い文字列を難読化][string-encryption]し、逆コンパイルされたコードの単純な検索不可能にする機能。
  * [所有権と配布文字列をアセンブリに慎重に埋め込み][watermarking] (ソフトウェア透かし)、不正なソフトウェア リークのソースを判断できる機能。
  * [複数のアセンブリを組み合わせ][linking]て、懸案事項の分離を除去することで、攻撃者がコード要素の役割を判断するのをさらに困難にする機能。
  * [使用されていないコードをアプリケーションから自動的に削除][pruning]して、付属される機密性の高いコードの量を減らす機能。
* *アプリケーション整合性の保護*
  * その他の[アプリケーション保護動作][check-actions]。
  * アプリケーションの有効期限前の警告期間を指定する機能。
  * 有効期限の警告期間中、または有効期限後にアプリケーション コードを通知する機能。
  * 製品利用統計情報の暗号化。
* *アプリケーション監視*
  * 一時的なネットワーク停止中に情報を収集し、収集された情報を保存する機能。
  * 個人を特定できる情報を収集する機能。
  * [機能の追跡][features]を無制限で使用可能。
  * ハンドルされない例外に加え、コード内でキャッチされ、スローされた例外を追跡する機能。
  * `.dll` アセンブリの例外を追跡する機能。
  * 製品利用統計情報の暗号化。

Dotfuscator Professional は業界標準の [.NET 難読化ツール][net-obfuscator]です。継続的なサポート、保守、製品の更新が必要な企業の開発者に適しています。
また、Dotfuscator Professional は Visual Studio との統合が強化され、商業目的の使用についてライセンスが付与されます。

Dotfuscator Professional の高度なアプリケーション保護機能の詳細については、PreEmptive Solutions の「[Dotfuscator Overview][product-about]」(Dotfuscator の概要) ページと、[Community Edition との比較][product-compare]のページを参照してください。
[preemptive.com では、完全にサポートされている評価版をリクエストして入手できます][eval]。

## <a name="see-also"></a>関連項目

[Dotfuscator CE の完全なユーザー ガイドのこのトピック][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions
[features]: https://www.preemptive.com/dotfuscator/pro/userguide/en/instrumentation_features.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html