---
title: レガシ言語サービスの機能拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129723"
---
# <a name="legacy-language-service-extensibility"></a>レガシ言語サービスの機能拡張
言語サービスは、IDE でソース コードを編集するため、言語固有のサポートを提供します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
 このセクションでは、構造と従来の言語サービスの実装について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスの移行](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Visual Studio 2008 から言語サービスを最新バージョンを更新する方法について説明します。  
  
 [従来の言語サービスの基本情報](../../extensibility/internals/legacy-language-service-essentials.md)  
 Visual Studio のプログラミング言語に統合する言語サービスを開発する方法に関する重要な情報を提供します。  
  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを作成するのに役立つトピックへのリンクを提供します。  
  
 [従来の言語サービスでの構文の色分け表示](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示をサポートする方法についてを説明します。  
  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Managed package framework (MPF) を使用してマネージ コードで言語の全機能を備えたサービスを実装する方法について説明します。  
  
 [シンボル参照ツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 ライブラリとすると、IDE でのシンボルのツリー ビューの参照を有効にするツールについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
 Visual Studio のエディターの概要を示します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 に関する情報と、リンク、Visual Studio Debugging SDK を作成し、プログラムをデバッグするために使用するデバッガー コンポーネントのカスタマイズに必要な情報が含まれています。