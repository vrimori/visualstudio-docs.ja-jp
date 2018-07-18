---
title: 使用して、サービスを提供する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351b5b5c0ab32ab7e8267864eddaae10459a23bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138341"
---
# <a name="using-and-providing-services"></a>使用して、サービスを提供します。
サービスは、次の 2 つの Vspackage の間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。 たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]提供、<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>サービス、VSPackage に読み込みます。 このサービスを提供、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>インターフェイスで、アクティビティ ログに書き込むために使用できます。 詳細については、次を参照してください。[する方法: アクティビティ ログを使用して](../extensibility/how-to-use-the-activity-log.md)です。  
  
 Vspackage を使用して独自のサービスを提供できる、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>インターフェイス.  
  
 Visual Studio には、次などの重要なサービスが提供しています。  
  
|IDE サービス|説明|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|基本的な機能、Vspackage、およびレジストリのサービス処理の IDE へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|基本の windowing と IDE では、ツールとドキュメント ウィンドウを作成する機能などの UI 関連の機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|プロジェクトを列挙、新しいプロジェクトの作成、およびプロジェクトの変更を監視する機能など、基本のソリューションに関連する機能を提供します。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [サービスの基本情報](../extensibility/internals/service-essentials.md)  
 Visual Studio サービスの重要な要素を表示します。  
  
 [方法: サービスを取得する](../extensibility/how-to-get-a-service.md)  
 要求する方法について説明します (使用する) サービス。  
  
 [方法: サービスを提供する](../extensibility/how-to-provide-a-service.md)  
 サービスを提供する方法について説明します。  
  
 [方法: Visual Studio の非同期サービスを提供する](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 非同期のサービスを提供する方法について説明します。  
  
 [方法: サービスのトラブルシューティング](../extensibility/how-to-troubleshoot-services.md)  
 一般的な問題について説明し、それらの解決策を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)