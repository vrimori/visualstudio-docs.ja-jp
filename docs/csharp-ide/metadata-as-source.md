---
title: "ソースとしてのメタデータ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 29b783e20925b3eaa4a7b0956fdcfdbcab06a328
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-as-source"></a>ソースとしてのメタデータ
ソースとしてのメタデータにより、読み取り専用のバッファーで C# ソース コードとして表示されるメタデータを見ることができます。 これにより、型とメンバー (実装を含まない) の宣言のビューが使用できるようになります。 プロジェクトまたはソリューションから利用できないソースコードを持つ型またはメンバーに対して **[定義へ移動]** コマンドを実行すると、ソースとしてのメタデータを表示することができます。  
  
> [!NOTE]
>  内部としてマークされている型またはメンバーに対して **[定義へ移動]** コマンドを実行しようとすると、統合開発環境 (IDE) には、参照元のアセンブリがフレンドかどうかに関係なく、ソースとしてのメタデータは表示されません。  
  
 コード エディターまたは **[コード定義]** ウィンドウで、メタデータをソースとして表示できます。  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>コード エディターでメタデータをソースとして表示  
 ソースコードが使用不可能な項目に対して **[定義へ移動]** コマンドを実行すると、ソースとして表示されるその項目のメタデータのビューを含むタブ付きドキュメントがコード エディターで表示されます。 末尾に **[メタデータから]**が続く型の名前がドキュメントのタブに表示されます。  
  
 たとえば、 **に対して** [定義へ移動] <xref:System.Console>コマンドを実行する場合は、その宣言に似ているものの、実装を持たない <xref:System.Console> のメタデータがコード エディターで C# ソース コードとして表示されます。  
  
 ![ソースとしてのメタデータ](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>[コード定義] ウィンドウでソースとしてメタデータを表示する  
 **[コード定義]** ウィンドウがアクティブまたは表示されている場合、コード エディター内のカーソルの下の項目と **[クラス ビュー]** または **[オブジェクト ブラウザー]** で選ばれた項目に対して、IDE は **[定義へ移動]**コマンドを自動的に実行します。 その項目のソース コードが使用できない場合、IDE は項目のメタデータをソースとして **[コード定義]** ウィンドウに表示します。  
  
 たとえば、コード エディターで <xref:System.Console> という単語内にカーソルを置く場合、 <xref:System.Console> のメタデータがソースとして **[コード定義]** ウィンドウに表示されます。 ソースは <xref:System.Console> 宣言に似ていますが、実装を持ちません。  
  
 **[コード定義]** ウィンドウで表示される項目の宣言を確認するには、その項目を右クリックし、 **[定義へ移動]**をクリックします。