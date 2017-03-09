---
title: "方法 : XML ドキュメントから XML スキーマを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : XML ドキュメントから XML スキーマを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML エディターを使用することで、XML ドキュメントから XML スキーマ定義言語 \(XSD\) スキーマを作成することができます。スキーマがどのように生成されるかは、XML インスタンス ドキュメントによって、次の方法で決定されます。  
  
-   XML ドキュメントにスキーマまたはドキュメント型定義 \(DTD\) が関連付けられていない場合は、新しい XML スキーマを推論するために XML ドキュメント内のデータが使用されます。  
  
-   関連する DTD が XML ドキュメントに含まれている場合は、外部 DTD および内部サブセットが、対応する XML スキーマに変換されます。  
  
-   インラインの XDR \(XML\-Data Reduced\) スキーマが XML ドキュメントに含まれている場合は、その XDR スキーマが、対応する XML スキーマに変換されます。  
  
 作成されたスキーマは次に、XML ドキュメントで IntelliSense を利用できるようにするために使用されます。  
  
 スキーマ推論エンジンの詳細については、「[XML スキーマの推論](../Topic/Inferring%20an%20XML%20Schema.md)」を参照してください。  
  
### XML スキーマを作成するには  
  
1.  XML インスタンス ドキュメントを XML エディターに読み込みます。  
  
2.  ツール バーの \[スキーマの作成\] ボタンをクリックします。  
  
     XML インスタンス ドキュメントで見つかった名前空間ごとに 1 つの XML スキーマ ドキュメントが作成され、開かれます。各スキーマは、一時的にその他のファイルとして開かれます。  
  
     スキーマは、ディスクに保存するか、プロジェクトに追加するか、破棄することができます。  
  
    > [!NOTE]
    >  XML エディターのショートカット メニューや \[XML\] メニューから、\[スキーマの作成\] コマンドを使用することもできます。  
  
## 参照  
 [XML エディター](../xml-tools/xml-editor.md)