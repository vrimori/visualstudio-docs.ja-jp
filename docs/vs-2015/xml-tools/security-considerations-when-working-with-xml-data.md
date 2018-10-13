---
title: XML データを使用する場合のセキュリティに関する考慮事項 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87f1fad820cbc7387779862c0c010b01cab0303e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302472"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML データを使用するときのセキュリティに関する考慮事項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このトピックでは、XML エディターや XSLT デバッガーを使用する際に知っておく必要があるセキュリティの問題について説明します。  
  
## <a name="xml-editor"></a>XML エディター  
 XML エディターは、Visual Studio のテキスト エディターに基づいています。 XML エディターは通常、<xref:System.Xml> クラスと <xref:System.Xml.Xsl> クラスに依存して XML プロセスを処理します。  
  
-   XSLT 変換は、新しいアプリケーション ドメインで実行されます。 XSLT 変換は*サンド ボックス化された*; XSLT スタイル シートがある場所に基づいて制限されたアクセス許可を決定する、コンピューターのコード アクセス セキュリティ ポリシーを使用する、します。 たとえば、インターネット上にあるスタイル シートは最も制限されたアクセス許可を持ち、ユーザーのハード ディスクにコピーされているスタイル シートは "完全な信頼" で実行されます。  
  
-   <xref:System.Xml.Xsl.XslCompiledTransform> クラスは、XSLT を Microsoft Intermediate Language (MSIL) にコンパイルし、実行時の処理速度を高めるために使用されます。  
  
-   カタログ ファイルで外部の場所を指し示すスキーマは、XML エディターが最初に読み込みを行うときに自動的にダウンロードされます。 <xref:System.Xml.Schema.XmlSchemaSet> クラスは、スキーマをコンパイルするために使用されます。 XML エディターに付属するカタログ ファイルには、外部のスキーマへのリンクは記述されていません。 XML エディターでスキーマ ファイルをダウンロードする前に、ユーザーは外部スキーマへの参照を明示的に追加する必要があります。 HTTP ダウンロードを使用して無効にできる、**その他のツール オプション**ページ、XML エディターの。  
  
-   XML エディターは、<xref:System.Net> クラスを使用してスキーマをダウンロードします。  
  
## <a name="xslt-debugger"></a>XSLT デバッガー  
 XSLT デバッガーは、Visual Studio のマネージ デバッグ エンジンと、<xref:System.Xml> および <xref:System.Xml.Xsl> 名前空間のクラスを使用します。  
  
-   XSLT デバッガーは、それぞれの XSLT 変換をサンドボックスで保護されたアプリケーション ドメインで実行します。 コンピューターのコード アクセスに関するセキュリティ ポリシーを使用し、XSLT スタイル シートが置かれている場所に基づいて、アクセス許可の制限が決定されます。 たとえば、インターネット上にあるスタイル シートは最も制限されたアクセス許可を持ち、ユーザーのハード ディスクにコピーされているスタイル シートは "完全な信頼" で実行されます。  
  
-   XSLT スタイル シートは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用してコンパイルされます。  
  
-   XSLT 式エバリュエーターは、マネージ デバッグ エンジンによって読み込まれます。 マネージ デバッグ エンジンは、すべてのコードがユーザーのローカル コンピューターから実行されることを前提としています。 そのため、<xref:System.Xml.Xsl.XslCompiledTransform> クラスによって XSLT ファイルがユーザーのコンピューターにダウンロードされます。 実行特権で評価が行われる可能性は、制限されたアクセス許可を使用して、新しいアプリケーション ドメインですべての XSLT 変換を実行することにより軽減されます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション ドメイン](http://msdn.microsoft.com/en-us/39e57d07-a740-4cd4-ae82-e119ea3856c1)



