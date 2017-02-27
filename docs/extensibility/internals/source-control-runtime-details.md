---
title: "ソース コントロールのランタイムの詳細 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理 [Visual Studio SDK] ランタイムの詳細"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ソース コントロールのランタイムの詳細
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトがを使用してユーザーがソース管理プロジェクトにファイルを追加するまたはウィザードなどオートメーション コントローラーとソース管理に追加されます。  プロジェクトは独自のソース管理下にあることを指定できません ; これはソース管理をサポートし手動で追加する必要があります。  
  
## パッケージ ソース管理に登録  
 プロジェクト ファイルがソース管理に追加すると環境はソース管理システムでクッキーとして使用される 4 種類の不透明な文字列を指定するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> を呼び出します。  プロジェクト ファイルに次の文字列を格納します。  これらの文字列はプロジェクトのスタートアップのソース管理のスタブ \(ソース管理パッケージを管理する Visual Studio コンポーネント\) に <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> の呼び出しを渡す必要があります。  これにより適切なソース管理パッケージを読み込み`IVsSccManager2::RegisterSccProject` の実装に呼び出しが転送されます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [ソース管理をサポートします。](../../extensibility/internals/supporting-source-control.md)