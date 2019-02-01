---
title: セキュリティ
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 40e751fa3edb74df01a9b8a2b0aa4643304f17dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771012"
---
# <a name="security-in-visual-studio"></a>Visual Studio におけるセキュリティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

セキュリティについては、設計から配置まで、アプリケーション開発のあらゆる段階で考慮する必要があります。 まず、Visual Studio をできるだけ安全に実行します。 「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。

 安全なアプリケーションを効果的に開発するためには、セキュリティの概念と、開発対象となるプラットフォームのセキュリティ機能について、基本事項を理解しておく必要があります。 さらに、安全なコーディング技法を身に付ける必要もあります。

## <a name="understanding-security"></a>セキュリティについて
 [セキュリティ](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) .NET Framework のコード アクセス セキュリティ、ロール ベース セキュリティ、セキュリティ ポリシー、およびセキュリティ ツールについて説明します。

 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (コードを守るためにすべての開発者が知る必要のある、セキュリティに関するヒント上位 10 項目): データまたはシステムに対する攻撃を防ぐために注意しなければならない問題について説明します。

## <a name="coding-for-security"></a>セキュリティに配慮したコーディング
 セキュリティ脆弱性の原因となるコーディング エラーのほとんどは、ユーザー入力に対する根拠のない仮定や、開発対象のプラットフォームに対する不十分な知識に起因しています。

 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177): セキュリティ問題に対処するためのコンポーネント分類ガイドラインを示します。

 [Security Best Practices](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) (セキュリティのベスト プラクティス): バッファー オーバーランと、Microsoft Visual C++ のセキュリティ チェック機能の詳細について説明します。この機能は、コンパイル時に /GS フラグを指定することによって利用できます。
