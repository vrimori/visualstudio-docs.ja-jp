---
title: Dotfuscator の機能
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, 難読化, .NET, 無料, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio 2017 に含まれる無料の Dotfuscator Community Edition の機能について説明します。
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b532bed6a20bd0fe79d4cdb820e9bcd5f15d1d8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935632"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator の機能

このページでは、Dotfuscator Community Edition (Dotfuscator CE) の機能と、[アップグレード][upgrades]で使用できる高度なオプションの参照を中心に説明します。

Dotfuscator は、.NET アプリケーションの*ビルド後*システムです。
Dotfuscator CE を使用すると、Visual Studio のユーザーは[アセンブリを難読化][obfuscation]し、[アクティブな防御策][checks]をアプリケーションに挿入することができます。その際に Dotfuscator が元のソース コードにアクセスする必要はありません。
Dotfuscator は、複数層の保護戦略を作成して複数の方法でアプリケーションを保護しています。

Dotfuscator CE は、[Universal Windows Platform (UWP)][uwp]、[Xamarin][xamarin] など、多様な .NET アセンブリとアプリケーションの種類をサポートしています。

## <a name="intellectual-property-protection"></a>知的財産の保護

アプリケーションの設計、動作、および実装は、知的財産 (IP) の形式です。
ただし、.NET Framework 用に作成されたアプリケーションは本質的に開いた本のようなものです。[.NET アセンブリには高レベルのメタデータと中間コードが含まれているので][assemblies]、簡単にリバース エンジニアリングできます。

Dotfuscator CE には、[名前の変更][renaming]の形式で基本的な [.NET 難読化][obfuscation]が含まれています。
Dotfuscator でコードを難読化すると、重要な命名に関する情報が非公開になるので、リバース エンジニアリングによるソース コードへの不正アクセスのリスクが軽減されます。
難読化は、開発者が調査からコードを保護する努力をしていることも示します。これは、IP が企業秘密として合法的に保護されていることを確認する上で重要な手順です。

Dotfuscator CE の多数ある[アプリケーション整合性保護機能](#application-integrity-protection)を使用すると、リバース エンジニアリングをさらに防ぐことができます。
たとえば、不正なアクターが、プログラムのロジックを理解するために、アプリケーションの実行中のインスタンスにデバッガーをアタッチしようとすることがあります。
Dotfuscator は[デバッグ対策の動作][debug]をアプリケーションに挿入してこの攻撃を防ぐことができます。

## <a name="application-integrity-protection"></a>アプリケーション整合性の保護

ソース コードの保護だけでなく、アプリケーションが指定したとおりに使用されていることを確認することも重要です。
攻撃者は、ライセンス ポリシーを回避する (つまりソフトウェアを違法コピーする)、アプリケーションが処理する機密データを盗用または操作する、またはアプリケーションの動作を変更する目的で、アプリケーションを乗っ取ろうとすることがあります。

Dotfuscator CE は、[改ざん防止][tamper]、[デバッグ防止][debug]、[ルート化されたデバイスの防止][root]の手段などの[アプリケーション検証コード][checks]をアセンブリに挿入できます。
無効なアプリケーションの状態が検出された場合、検証コードから[アプリケーション コードを呼び出し、適切な方法で状況に対処することができます][check-app]。
また、アプリケーションの無効な使用に対処するコードを作成したくない場合は、Dotfuscator でソース コードを変更することなく、[応答動作][check-action]を挿入できます。

これらの多くの方法は、評価版や試用版のソフトウェアの[有効期間][shelflife]を強制するためにも使用できます。

## <a name="see-also"></a>「

[Dotfuscator CE の完全なユーザー ガイドのこのトピック][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
