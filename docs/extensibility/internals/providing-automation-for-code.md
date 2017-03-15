---
title: "コードのための自動化を提供します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeModel オブジェクト"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# コードのための自動化を提供します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コードのオートメーション モデルを作成する必要はありません。  SDK 環境ではそのためのサンプルはありません。  コード モデルに追跡するために<xref:EnvDTE.CodeModel> のオブジェクトを参照してください。  
  
 コード モデルを使用するには内部のデータ構造によって決定されるインターフェイスを実装する必要があります。  オブジェクトは `IDispatch` のクラスから派生させる必要があります。  
  
 および <xref:EnvDTE.CodeModel> 拡張するオブジェクト <xref:EnvDTE.FileCodeModel> は<xref:EnvDTE.Project> のオブジェクトで使用できますが次のようになります。:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 `Project`および <xref:EnvDTE.ProjectItem> のオブジェクトが返すオブジェクトの一つ `CodeModel` または `FileCodeModel` のインターフェイスを実装することもできます。  プロジェクト システムに適したこのインターフェイスの機能を提供します。  
  
 メソッドなどの機能を追加したり`FileCodeModel` の標準 `CodeModel` とインターフェイスからされていないプロパティ標準から継承する独自のインターフェイスを作成します。  プロジェクト システムで説明するようにそれを検索するためにエンド ユーザーを検証します。  標準インターフェイスを返しますがあることがわかっている場合はユーザー `QueryInterface` のメソッドを呼び出すかまたはインターフェイスにキャストできます。  
  
## 参照  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)