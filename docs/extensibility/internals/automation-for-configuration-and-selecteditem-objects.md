---
title: 構成および SelectedItem オブジェクトのための自動化 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 90af8e941eb18a703974859ea4393fd84182077d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905651"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>構成および SelectedItem オブジェクトのための自動化
ビルドと選択した項目のプロセスを自動化できます。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="automation-for-builds"></a>ビルドの自動化  
 実装するときに提供されるオートメーション モデルをビルドまたは構成が<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>します。 詳しくは、「[ビルド構成について](../../ide/understanding-build-configurations.md)」をご覧ください。  
  
 VSPackage を作成して構成オプションを制御する場合は、オートメーション モデルを使用する必要があります。  
  
## <a name="automation-for-selecteditem"></a>SelectedItem のための自動化  
 実装を提供する必要はありません、`SelectedItem`オブジェクトの Visual Studio には、標準的な実装が含まれています。 ただし、実装、`SelectedItem`オブジェクトの場合します。 含むオブジェクトを実装する必要があります、`SelectedItem`インターフェイスし、への呼び出しに応答を返す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>メソッド`VSITEMID`に設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [オートメーション モデルに貢献します。](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [ビルド構成について](../../ide/understanding-build-configurations.md)