---
title: "Visual Studio におけるセキュリティ |Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 7a282fc04c1eb01f0c56b1d76880276fc270686d
ms.openlocfilehash: 96136c7223f3d5f78fff9bfe3106d48cab4dd44a
ms.lasthandoff: 03/01/2017

---
# <a name="security-in-visual-studio"></a>Visual Studio におけるセキュリティ
セキュリティについては、設計から配置まで、アプリケーション開発のあらゆる段階で考慮する必要があります。 まず、Visual Studio をできるだけ安全に実行します。 「[ユーザー アクセス許可と Visual Studio](../ide/user-permissions-and-visual-studio.md)」を参照してください。  
  
 安全なアプリケーションを効果的に開発するためには、セキュリティの概念と、開発対象となるプラットフォームのセキュリティ機能について、基本事項を理解しておく必要があります。 さらに、安全なコーディング技法を身に付ける必要もあります。  
  
## <a name="understanding-security"></a>セキュリティについて  
 [セキュリティ](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 .NET Framework のコード アクセス セキュリティ、ロール ベース セキュリティ、セキュリティ ポリシー、およびセキュリティ ツールについて説明します。  
  
 [コードを守るためにすべての開発者が知る必要のある、セキュリティに関するヒント上位&10; 項目](http://go.microsoft.com/fwlink/?LinkId=72877)  
 データまたはシステムに対する攻撃を防ぐために注意しなければならない問題について説明します。  
  
## <a name="coding-for-security"></a>セキュリティに配慮したコーディング  
 セキュリティ脆弱性の原因となるコーディング エラーのほとんどは、ユーザー入力に対する根拠のない仮定や、開発対象のプラットフォームに対する不十分な知識に起因しています。  
  
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 セキュリティ問題に対処するためのコンポーネント分類ガイドラインを示します。  
  
 [セキュリティ推奨事項](/visual-cpp/top/security-best-practices-for-cpp)  
 バッファー オーバーランと、Microsoft Visual C++ のセキュリティ チェック機能の詳細について説明します。この機能は、コンパイル時に /GS フラグを指定することによって利用できます。

## <a name="building-for-security"></a>セキュリティに配慮したビルド  
 セキュリティはビルド プロセスでも重要な考慮事項です。  いくつかの追加手順で、展開するアプリのセキュリティを改善し、不正なリバース エンジニアリング、なりすましなどの攻撃を防ぐことができます。

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 無料の PreEmptive Protection - Dotfuscator Community Edition を設定し、使用を開始して .NET アセンブリをリバース エンジニアリングと不正使用 (不正なデバッグなど) から保護する方法について説明します。
  
 [アセンブリおよびマニフェストへの署名の管理](managing-assembly-and-manifest-signing.md)  
 厳密な名前の署名について説明します。厳密な名前の署名を使用すると、ソフトウェア コンポーネントを一意に識別し、名前のなりすましを防ぐことができます。
