---
title: "使用して、サービスを提供する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>使用して、サービスを提供します。
サービスは、2 つの VSPackages 間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。 たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]は用意されています、<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>サービスすべての VSPackage に読み込みます</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>。 このサービスは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>アクティビティ ログへの書き込みに使用できるインターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>を提供します。 詳細については、次を参照してください。[方法:、動作状況ログを使用して](../extensibility/how-to-use-the-activity-log.md)します。  
  
 VSPackages は、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>.. インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>を使用して、独自のサービスを提供することができます。  
  
 Visual Studio には、次などの重要なサービスが提供しています。  
  
|IDE のサービス|説明|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|基本的な機能、vspackages にある、レジストリとサービス対応の IDE へのアクセスを提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|基本的なウィンドウおよびツールとドキュメント ウィンドウを作成する機能などの IDE での UI 関連の機能を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|プロジェクトの列挙、新しいプロジェクトの作成、およびプロジェクトの変更を監視する機能など、基本的なソリューション関連の機能を提供します。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [サービスの基礎](../extensibility/internals/service-essentials.md)  
 Visual Studio のサービスの重要な要素を表示します。  
  
 [方法: サービスを取得](../extensibility/how-to-get-a-service.md)  
 要求する方法について説明します (使用する) サービス。  
  
 [方法: サービスを提供](../extensibility/how-to-provide-a-service.md)  
 サービスを提供する方法について説明します。  
  
 [方法: Visual Studio の非同期サービスを提供](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 非同期のサービスを提供する方法について説明します。  
  
 [方法: サービスのトラブルシューティング](../extensibility/how-to-troubleshoot-services.md)  
 一般的な問題について説明し、それらの対処方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
