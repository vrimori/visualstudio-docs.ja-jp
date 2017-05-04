---
title: "ドキュメント レベルのカスタマイズのキャッシュ データ | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "キャッシュ (データを) [Visual Studio での Office 開発], データ キャッシュの概要"
  - "データ [Visual Studio での Office 開発], キャッシュ"
  - "データ [Visual Studio での Office 開発], ドキュメント レベルのソリューション"
  - "データ キャッシュ [Visual Studio での Office 開発], データ キャッシュの概要"
  - "データ アイランド [Visual Studio での Office 開発]"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発], データ モデル"
  - "ビュー [Visual Studio での Office 開発]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# ドキュメント レベルのカスタマイズのキャッシュ データ
  ドキュメント レベルのカスタマイズは、データを Office ドキュメントのビューから分離することを主要な目的としています。  データとは、数値やテキストなど、ドキュメントに格納されている情報のことです。  ビューとは、Microsoft Office Word および Microsoft Office Excel のユーザー インターフェイスとオブジェクト モデルを意味します。  
  
 Visual Studio では、データを*データ アイランド* \(*データ キャッシュ*ともいいます\) として埋め込むことによって、ドキュメント レベルのカスタマイズのビューから分離できます。  そのため Word または Excel を起動せずに、データを直接読み取ったり変更したりすることができます。  これは、Microsoft Office がインストールされていないサーバー上にある文書のデータを編集する必要がある場合に役立ちます。  Word および Excel はクライアント環境での使用が想定されており、サーバー上で実行するようには設計されていません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのカスタマイズの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」および「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
## キャッシュ データ プログラミング モデルの概要  
 データ アイランドには、ソリューション内のオブジェクトのうち特定の要件を満たすものを含めることができます。  そうしたオブジェクトには、<xref:System.Data.DataSet> オブジェクト、<xref:System.Data.DataTable> オブジェクト、および <xref:System.Xml.Serialization.XmlSerializer> クラスによってシリアル化できるオブジェクトが含まれます。  詳細については、[キャッシュされたデータ](../vsto/caching-data.md) を参照してください。  
  
 キャッシュされたデータのビューを提供するには、ドキュメント上の Windows フォーム コントロールと*ホスト コントロール*をデータ アイランド内のオブジェクトにバインドします。  データ アイランドとデータがバインドされたコントロールは、それらの間のデータ バインディングによって同期が維持されます。  コントロールから独立した検証コードをデータに追加することもできます。  詳細については、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」を参照してください。  
  
 ホスト コントロールは、Word および Excel のオブジェクト モデルに属するネイティブ オブジェクトの拡張バージョンです。  ネイティブ オブジェクトとは異なり、ホスト コントロールはマネージ データ オブジェクトに直接バインドできます。  詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」および「[Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)」を参照してください。  
  
## サーバー上のキャッシュされたデータへのアクセス  
 ドキュメント内のキャッシュされたデータにアクセスするには、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用します。  このクラスは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれており、Excel や Word を実行せずにサーバー上で使用できます。  キャッシュされたデータを変更した後でユーザーがドキュメントを開くと、そのデータにバインドされているコントロールに変更が自動的に反映されるため、更新されたデータが表示されます。  詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
 クライアントでの表示にのみ Excel と Word を使用し、サーバーのデータへの書き込みには使用しません。  Excel や Word をサーバーにインストールしておく必要はありません。  このため、スケーラビリティが向上し、データ アイランドが含まれるドキュメントを迅速にバッチ処理できます。  
  
## オフラインで使用するためのデータ キャッシング  
 データをデータ アイランドに格納することにより、オフライン作業が可能になります。  ユーザーが最初にドキュメントを開いたとき、またはサーバーからドキュメントを要求したときに、データ アイランドには最新のデータが格納されています。  データ アイランドはドキュメント内にキャッシュされた後で、オフラインで利用可能になります。  ユーザー \(ユーザーのコード\) は、オンライン接続できない状態であってもデータを操作できます。  ユーザーが再接続すると、データの変更がサーバーのデータ ソースに反映されます。  
  
## キャッシュされたデータとカスタム XML 部分の比較  
 カスタム XML 部分は、任意の XML コードをドキュメントに格納する手段として、2007 Microsoft Office system で導入されました。  カスタム XML 部分はデータ キャッシュと同じシナリオの多くで役立ちますが、データ アイランドとカスタム XML 部分の間にはいくつかの相違点があります。  カスタム XML 部分の詳細については、「[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
 データ アイランドとカスタム XML 部分の主な相違点と類似点を次の表に示します。  
  
||データ キャッシュ|カスタム XML 部分|  
|-|---------------|-----------------|  
|これらの機能を使用できる Office アプリケーション|以下のアプリケーションのドキュメント レベルのカスタマイズ<br /><br /> -   Excel<br />-   Word|以下のアプリケーションのドキュメント レベルのソリューションおよびアプリケーション レベルのソリューション<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|格納できるデータの種類|カスタマイズ アセンブリ内の特定の要件を満たすパブリック オブジェクト。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。|XML データ|  
|Microsoft Office アプリケーションを起動することなくデータにアクセスできるかどうか|[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] に含まれる <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してアクセスできます。|<xref:System.IO.Packaging> 名前空間内のクラスを使用するか、または Open XML Formats SDK を使用してアクセスできます。|  
  
## 参照  
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [Visual Studio の Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  