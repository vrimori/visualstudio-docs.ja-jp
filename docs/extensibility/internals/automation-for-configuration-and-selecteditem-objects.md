---
title: "構成と SelectedItem オブジェクト用のオートメーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42a3b8bdd8930c9006ba49fd0f2e2dd2491b38cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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