---
title: アプリケーションのグローバライズとローカライズ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9abcb55d49b84a97ad7eae241547317d74cc6f71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="globalizing-and-localizing-applications"></a>アプリケーションのグローバライズとローカライズ

アプリケーションを各国のユーザー向けに配布する場合は、デザイン段階や開発段階で留意する必要のある事項がいくつかあります。 アプリケーションを国際対応にする計画がない場合でも、事前に多少の配慮をしておくと、アプリケーションの将来のバージョンで計画が変更になったときに役立ちます。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に組み込まれたサービスを利用すると、Visual Studio でマネージ開発を使用して、異なるロケールに適応できる単一のアプリケーションを簡単に開発できます。

## <a name="resources"></a>リソース

 Visual Studio は、設計の初期段階から、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に組み込まれたサービスを活用して各国用アプリケーションを簡単に開発できるようにすることを目指してきました。 次に示す各記事では、Visual Studio に組み込まれた国際化機能について紹介します。

 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) Visual Studio と [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を使用した国際市場向けのソフトウェア開発についての概念を説明します。

 [アプリケーションのローカライズ](../ide/localizing-applications.md) 特定のカルチャを対象としたアプリケーションのカスタマイズに関するページのリンクが掲載されています。

 [アプリケーションのグローバル化](../ide/globalizing-applications.md) 複数のカルチャをサポートするアプリケーションの作成について説明するページのリンクが掲載されています。

## <a name="see-also"></a>関連項目

- [推奨される国際対応アプリケーション開発手順](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c) 各国のユーザー向けのプログラミングについての背景情報を示します。
- [クラス ライブラリの概要](/dotnet/standard/class-library-overview) 開発プロセスを高速化および最適化し、システム機能へのアクセスを提供する、クラス、インターフェイス、および値型について説明します。
- <xref:System.Globalization> は、この名前空間内のクラスを示します。これらのクラスは、言語、国/地域、使用するカレンダー、日付形式、通貨と数値、文字列の並べ替え順などのカルチャ情報を定義します。
- <xref:System.Resources> は、この名前空間内のクラスとインターフェイスを示します。開発者は、これらのクラスやインターフェイスを使用して、アプリケーションで使用されるカルチャ固有の各種リソースを作成、保管、および管理できます。