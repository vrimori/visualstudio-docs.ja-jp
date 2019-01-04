---
title: エディターと言語サービス拡張機能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4182af1731dec583a555031b90be1315e6a5d9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927482"
---
# <a name="editor-and-language-service-extensions"></a>エディターと言語サービス拡張機能
Visual Studio コード エディターのほとんどの機能を拡張することができます。 エディターでは、Windows Presentation Foundation (WPF) に基づいており、マネージ コードで記述されました。 この設計は、以前のバージョンの Visual Studio でデザインから異なる場合は、ほとんどの同じ機能を提供します。 エディターを拡張するには、Managed Extensibility Framework (MEF) を使用します。  
  
 Visual Studio SDK は、アダプターと呼ばれる*shim*以前のバージョン用に作成された Vspackage をサポートするためにします。 ただし、既存の VSPackage があればより優れたパフォーマンスと信頼性を取得する新しいテクノロジに更新することお勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[エディターの項目テンプレートを使用した拡張機能を作成します。](../extensibility/creating-an-extension-with-an-editor-item-template.md)|エディター項目テンプレートの使用方法を紹介します。|  
|[エディターと言語サービスを拡張します。](../extensibility/extending-the-editor-and-language-services.md)|設計とコア エディターの機能を紹介し、それを拡張する方法について説明するドキュメントにリンクします。|  
|[エディターでのレガシー インターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)|既存のコードからコア エディターにアクセスする方法を説明するドキュメントにリンクします。|  
|[カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)|カスタム エディターを作成する方法を説明するドキュメントへのリンク。|  
|[従来の言語サービス拡張機能](../extensibility/internals/legacy-language-service-extensibility.md)|プログラミング言語を Visual Studio に統合する方法を説明するドキュメントにリンクします。|  
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) が導入されています。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) をについて説明します。|