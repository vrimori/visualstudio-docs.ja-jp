---
title: 従来の言語サービス拡張機能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 691592ce59d4495af3b248dde4ebfc9af1665d55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015031"
---
# <a name="legacy-language-service-extensibility"></a>従来の言語サービスの機能拡張
言語サービスは、IDE でソース コードを編集するため、言語固有のサポートを提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターと言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)します。  
  
 このセクションでは、構造と従来の言語サービスの実装について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスの移行](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 言語サービスを Visual Studio 2008 から最新バージョンに更新する方法について説明します。  
  
 [従来の言語サービスの基本情報](../../extensibility/internals/legacy-language-service-essentials.md)  
 Visual Studio のプログラミング言語に統合する言語サービスを開発する方法に関する重要な情報を提供します。  
  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを作成するのに役立つトピックへのリンクを提供します。  
  
 [従来の言語サービスでの構文の色分け表示](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示のサポートについてを説明します。  
  
 [従来の言語サービスの実装](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Managed package framework (MPF) を使用して、マネージ コードでのフル機能の言語サービスを実装する方法について説明します。  
  
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 ライブラリと、IDE でシンボルのツリー ビューを参照するためのツールについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
 Visual Studio エディターの概要を示します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 Visual Studio Debugging SDK を作成し、プログラムをデバッグするために使用するデバッガー コンポーネントのカスタマイズに必要な情報を含むに関する情報とリンクを提供します。