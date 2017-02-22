---
title: "ソース コントロールの設計の決定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理 [Visual Studio SDK] 設計上の決定"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース コントロールの設計の決定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のデザインの決定はプロジェクトでソース管理を実行するときに考慮する必要があります。  
  
## 情報はプライベート共有されます。  
 ユーザーが行うことができる最も重要なデザインの決定が情報を共有できません。また既にプライベートな要素です。  たとえばプロジェクトのファイルの一覧が共有されますがこのファイルの一覧は一部のユーザーはファイルが必要な場合もあります。  コンパイラ設定が共有されますがスタートアップ プロジェクトは通常プライベートです。  設定にはオーバーライドと共有する場合もプライベート共有されます。  デザインではプライベート項目はソリューションのユーザー オプション \(.suo\) ファイルなどの [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] にチェックされません。  作成した .suo ファイルなどファイルに個人情報を保存することや特定のファイルVisual Basic 用の Visual C\# のたとえば.csproj.user ファイルまたは .vbproj.user ファイルを確認します。  
  
 この決定は包括的ではなく項目と項目単位で行うことができます。  
  
## プロジェクトは特殊なファイルが含まれていますか。  
 もう一つの重要なデザインの決定はプロジェクト構造が特殊ファイルを使用するかです。  特殊ファイルはソリューション エクスプローラーとチェックインおよびチェック アウト ダイアログ ボックスに表示されるファイルの下にある隠しファイルです。  特殊ファイルを使用する場合は次のガイドラインに従います。:  
  
1.  あるノードのプロジェクト ファイル自体にプロジェクト ルートで特殊ファイルを関連付けないください。  プロジェクト ファイルでは一つのファイルである必要があります。  
  
2.  特殊なファイルがプロジェクトに追加削除または名前変更されたときに<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> の適切なイベントを示すフラグが設定されたファイルは特殊なファイルであることを適用する必要があります。  これらのイベントは <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> の適切なメソッドを呼び出すプロジェクトに応じて環境によって呼び出されます。  
  
3.  プロジェクトまたはファイルがエディターの <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> を呼び出すとそのファイルに関連付けられている特殊ファイルが自動的にチェックされません。  親ファイルとともに特殊ファイルを渡します。  環境が適切にチェック アウトの UI の特殊なファイルを非表示にするに渡されるすべてのファイルの関係を検出します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [ソース管理をサポートします。](../../extensibility/internals/supporting-source-control.md)