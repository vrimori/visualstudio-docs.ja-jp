---
title: オートメーション [オプション] ページのサポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36783227ceed5d1b074937684d42c4486ec58dda
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926019"
---
# <a name="automation-support-for-options-pages"></a>[オプション] ページのオートメーションをサポートします。
Vspackage は、ユーザー設定を提供できる**オプション** ダイアログ ボックス、**ツール**メニュー (**ツール オプション**ページ) で[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自動化に利用できるように、モデル。  
  
## <a name="tools-options-pages"></a>[ツール] メニューの [オプション] ページ  
 作成する、**ツール オプション** ページで、VSPackage の VSPackage の実装により、環境に返されるユーザー コントロールの実装を提供する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド。 (または、マネージ コード、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッドです)。 
  
 これは省略可、ただし、オートメーション モデルからこの新しいページにアクセスできるように強くお勧めします。 次の手順で行うことができます。  
  
1. 拡張、 <xref:EnvDTE._DTE.Properties%2A> IDispatch から派生したオブジェクトの実装を使用してオブジェクト。  
  
2. 実装を返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッド (またはマネージ コードに対して、<xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>メソッド) IDispatch から派生したオブジェクトにします。  
  
3. Automation の消費者を呼び出すときに、<xref:EnvDTE._DTE.Properties%2A>カスタム メソッド**オプション**プロパティ ページで、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、ユーザー設定を取得する**ツール オプション**ページのオートメーション実装です。  
  
4. 各を提供する VSPackage のオートメーション オブジェクトを使用して<xref:EnvDTE.Property>によって返される<xref:EnvDTE._DTE.Properties%2A>します。  
  
   カスタムの実装サンプル**ツール オプション**ページを参照してください[VSSDK のサンプル](http://aka.ms/vs2015sdksamples)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト オブジェクトを公開します。](../../extensibility/internals/exposing-project-objects.md)