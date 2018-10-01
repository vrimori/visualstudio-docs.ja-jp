---
title: オートメーション コードの提供 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 456927337331c15b3392b03175d83f2a63f87e77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533256"
---
# <a name="providing-automation-for-code"></a>コードのオートメーションの提供
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[オートメーション コードを提供する](https://docs.microsoft.com/visualstudio/extensibility/internals/providing-automation-for-code)します。  
  
コードのオートメーション モデルを作成する必要はありません。 環境の SDK では、そのため、サンプルは提供されません。 コード モデルを把握するには、次を参照してください。、<xref:EnvDTE.CodeModel>オブジェクト。  
  
 コード モデルを実装するには、内部データ構造によって決定されるインターフェイスを実装する必要があります。 オブジェクトから派生する必要があります、`IDispatch`クラス。  
  
 オブジェクトを拡張すると、<xref:EnvDTE.CodeModel>と<xref:EnvDTE.FileCodeModel>から利用できる、<xref:EnvDTE.Project>オブジェクトし、次のようになります。  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 実装することができます、`CodeModel`または`FileCodeModel`から返すオブジェクトのインターフェイス、`Project`と<xref:EnvDTE.ProjectItem>オブジェクト。 このプロジェクト システムの適切なインターフェイスからの機能を提供します。  
  
 メソッドやプロパティなどの機能を追加する場合をからは入手できず、標準`CodeModel`と`FileCodeModel`インターフェイスは、standard から継承するインターフェイスを作成します。 エンドユーザーが探しに知っていただけるように、プロジェクト システムでドキュメントを必ず。 標準のインターフェイスを返しますが、ユーザーが呼び出すことができます、`QueryInterface`メソッドまたは存在することがわかっている場合、インターフェイスにキャストします。  
  
## <a name="see-also"></a>関連項目  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)

