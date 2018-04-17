---
title: エディターおよび言語サービスの拡張機能 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="editor-and-language-service-extensions"></a>エディターと言語サービスの拡張機能
Visual Studio code エディターのほとんどの機能を拡張することができます。 エディターは Windows Presentation Foundation (WPF) に基づいており、マネージ コードで記述されました。 この設計は、以前のバージョンの Visual Studio でデザインから異なる場合は、同じ機能のほとんどを提供します。 エディターを拡張するには、Managed Extensibility Framework (MEF) を使用します。  
  
 Visual Studio SDK は、アダプターと呼ばれる*shim*以前のバージョン用に作成された Vspackage をサポートするためにします。 ただし、既存の VSPackage があればより優れたパフォーマンスと信頼性を取得する新しい技術を更新することお勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)|エディター項目テンプレートの使用方法の概要です。|  
|[エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)|設計とコア エディターの機能を紹介し、それを拡張する方法を示しているドキュメントにリンクします。|  
|[エディターでの従来のインターフェイス](../extensibility/legacy-interfaces-in-the-editor.md)|既存のコードからコア エディターにアクセスする方法を説明するドキュメントへのリンク。|  
|[カスタム エディターとデザイナーの作成](../extensibility/creating-custom-editors-and-designers.md)|カスタム エディターを作成する方法を説明するドキュメントへのリンク。|  
|[従来の言語サービスの機能拡張](../extensibility/internals/legacy-language-service-extensibility.md)|Visual Studio プログラミング言語に統合する方法を説明するドキュメントへのリンク。|  
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) を紹介します。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) をについて説明します。|