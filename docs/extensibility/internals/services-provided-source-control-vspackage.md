---
title: 提供されるサービス (ソース コントロール VSPackage) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a52ffa7067a91582d8bfe31e09d6b03be54c4ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="services-provided-source-control-vspackage"></a>提供されるサービス (ソース コントロール VSPackage)
サービスは、Vspackage 間および Visual Studio 統合開発環境 (IDE) と、インストールされている Vspackage 間に機能を共有する主要なメカニズムです。 サービスと、Visual Studio IDE の重要度の詳細については、次を参照してください。[を使用するとサービスを提供する](../../extensibility/using-and-providing-services.md)です。  
  
## <a name="the-source-control-service"></a>ソース管理サービス  
 Visual Studio には、サービス、IDE レベルのサービスおよびパッケージ レベルのサービスの 2 つのレイヤーが用意されています。 Visual Studio IDE は、ネイティブ IDE レベルのサービスを提供します。 ソース管理パッケージでは、これらのサービスの一部を消費します。 VSPackage としてソース管理パッケージでは、独自のプライベートはソース管理サービスを提供することにより、ソース管理機能を共有します。 ソース管理パッケージは、Visual Studio IDE で使用できるコントラクトの形式でによって実装されたソース コントロールに関連するインターフェイスのセットをカプセル化します。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)