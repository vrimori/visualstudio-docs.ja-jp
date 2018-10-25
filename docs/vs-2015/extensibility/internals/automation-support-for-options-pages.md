---
title: オートメーション [オプション] ページのサポート |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ded80c0bcb7ac8246d1ac620aa936d63ecb3b04d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902374"
---
# <a name="automation-support-for-options-pages"></a>オプション ページのオートメーションのサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage は、ユーザー設定を提供できます**オプション** ダイアログ ボックス、**ツール**メニュー ([ツール オプション] ページ) で[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]し、オートメーション モデルを利用できるようにします。  
  
## <a name="tools-options-pages"></a>ツール オプション ページ  
 作成する、**ツール オプション** ページで、VSPackage の VSPackage の実装により、環境に返されるユーザー コントロールの実装を提供する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド (またはマネージ コードに対する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッドの場合)。  
  
 これは省略可、ただし、オートメーション モデルからこの新しいページにアクセスできるように強くお勧めします。 これは、次の手順を行うことができます。  
  
1. 拡張、 <xref:EnvDTE._DTE.Properties%2A> IDispatch から派生したオブジェクトの実装を使用してオブジェクト。  
  
2. 実装を返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッド (またはマネージ コードに対して、<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>メソッド) IDispatch から派生したオブジェクトにします。  
  
3. Automation の消費者を呼び出すときに、<xref:EnvDTE._DTE.Properties%2A>カスタム メソッド**オプション**プロパティ ページで、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、ユーザー設定を取得する**ツール オプション**ページのオートメーション実装です。  
  
4. 各を提供する VSPackage のオートメーション オブジェクトを使用して<xref:EnvDTE.Property>によって返される<xref:EnvDTE._DTE.Properties%2A>します。  
  
   カスタム ツール オプション ページを実装するサンプルについては、次を参照してください。 [VSSDK のサンプル](../../misc/vssdk-samples.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト オブジェクトの公開](../../extensibility/internals/exposing-project-objects.md)

