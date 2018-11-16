---
title: 構成および SelectedItem オブジェクトのための自動化 |Microsoft Docs
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
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 612916da7922900a1054d785dad86ed448aa1f12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733467"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>構成および SelectedItem オブジェクトのためのオートメーション
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ビルドと選択した項目のプロセスを自動化できます。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="automation-for-builds"></a>ビルドの自動化  
 実装するときに提供されるオートメーション モデルをビルドまたは構成が<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>します。 詳しくは、「[ビルド構成について](../../ide/understanding-build-configurations.md)」をご覧ください。  
  
 VSPackage を作成して構成オプションを制御する場合は、オートメーション モデルを使用する必要があります。  
  
## <a name="automation-for-selecteditem"></a>SelectedItem のための自動化  
 実装を提供する必要はありません、`SelectedItem`オブジェクトの Visual Studio には、標準的な実装が含まれています。 ただし、実装、`SelectedItem`オブジェクトの場合します。 含むオブジェクトを実装する必要があります、`SelectedItem`インターフェイスし、への呼び出しに応答を返す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSITEMID を持つメソッドに設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [オートメーション モデルに貢献します。](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [ビルド構成について](../../ide/understanding-build-configurations.md)

