---
title: Visual Studio でのアプリケーションのセキュリティの維持
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee7a90804c2161fe927bebc2b2f1af45862b8ccd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="maintain-security"></a>セキュリティの維持

セキュリティの価値は継続的な警戒にある、とよく言われます。 アプリケーションのデザイン時や開発時にいかに万全のセキュリティ対策を行っても、配置後にセキュリティの欠陥が明らかになる可能性も想定する必要があります。 アプリケーションの監査とイベント ログの分析から、それまでわからなかった欠陥が見つかることもあります。

さらに、自分が作成したアプリケーションのセキュリティを維持するだけでなく、アプリケーションが実行されるプラットフォームやアプリケーションが依存している他の製品についても、セキュリティの脅威や欠陥に関する最新情報に目を配る必要があります。

[セキュリティ、プライバシー、アカウント](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;ウイルス、パスワード、保護者による制限、ファイアウォール、ドライブの暗号化に関する情報など、セキュリティ、プライバシー、ユーザー アカウントについてのヘルプです。

[マイクロソフト セキュリティ更新プログラムの掲示板](https://technet.microsoft.com/security/bulletins.aspx)&mdash;このページでは、過去に発表された情報を簡単に見つけることができます。 IT 専門家を対象に、セキュリティ更新プログラムに関する詳しい情報を提供しています。

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) は、ホーム ユーザー、企業ユーザー、または管理者を対象とするツールです。このツールを使用すると、Windows ベースのコンピューターでよくあるセキュリティ設定の間違いを見つけることができます。