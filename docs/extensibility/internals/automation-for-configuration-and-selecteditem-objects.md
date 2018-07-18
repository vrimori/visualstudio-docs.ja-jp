---
title: 構成と SelectedItem オブジェクト用のオートメーション |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4ac269664136aed51542e53900ffc1c87f21fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128203"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>構成と SelectedItem オブジェクト用のオートメーション
ビルドと選択した項目のプロセスを自動化できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="automation-for-builds"></a>ビルドの自動化  
 ビルドまたは構成が実装するときに表示されるオートメーション モデル<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>です。 詳しくは、「[ビルド構成について](../../ide/understanding-build-configurations.md)」をご覧ください。  
  
 VSPackage を作成して構成オプションを制御する場合は、オートメーション モデルを使用する必要があります。  
  
## <a name="automation-for-selecteditem"></a>SelectedItem の自動化  
 実装を提供する必要はありません、`SelectedItem`オブジェクトの Visual Studio には、標準的な実装が含まれているためです。 ただし、実装することができます、`SelectedItem`オブジェクトのかどうかにできます。 格納するオブジェクトを実装する必要があります、`SelectedItem`インターフェイスし、への呼び出しに応答を返す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSITEMID を持つメソッドに設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [オートメーション モデルに貢献しています。](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [ビルド構成について](../../ide/understanding-build-configurations.md)