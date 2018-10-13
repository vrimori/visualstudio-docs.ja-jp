---
title: ポート シェイプのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dcb6ad091d0b65e5b368f5822659a909e9f4c42a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290707"
---
# <a name="properties-of-port-shapes"></a>ポート シェイプのプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ポート図形を使用すると、生成されたデザイナーでのドメイン クラスを表します。  
  
 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。  
  
 ポート図形では、次の表に記載されているプロパティがあります。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|[塗りつぶしの色]|この図形の塗りつぶしの色。|白|  
|塗りつぶしのグラデーション モード|この図形の塗りつぶしのグラデーション モード。|[水平方向]|  
|geometry|この図形 (四角形、角丸四角形、楕円、または円) のジオメトリ。|四角形|  
|既定の接続ポイントします。|場合`True`図形を使用して、top、bottom、left、および右の接続は、生成されたデザイナーで参照します。|False|  
|アウトラインの色|この図形のアウトラインの色。|黒|  
|輪郭の実線/点線スタイル|(実線、ダッシュ、ドット、DashDot、DashDotDot、またはカスタム) は、この図形の輪郭の実線/点線スタイル。|[実線]|  
|外枠の太さ|この図形のアウトラインの太さです。|0.03125|  
|テキストの色|この図形に関連付けられているテキスト デコレーターに使用される色。|黒|  
|アクセス修飾子|クラスのアクセスのレベル (`public`または`internal`)。|Public|  
|カスタム属性|この図形から生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|  
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください[をオーバーライドすると、生成されたクラスを拡張する。](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターは、ソース コードで提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|  
|継承修飾子|ポートから生成されるソース コードのクラスの継承の種類について説明します (`none`、`abstract`または`sealed`)。|none|  
|ベース ポート|この図形の基本クラス。|(なし)|  
|名前|この図形の名前。|現在の名前|  
|名前空間|この図形に関連付ける名前空間。|現在の名前空間|  
|ツール ヒントの種類|(固定、変数、またはなし)、ツールヒントを定義する方法。 、しの値を固定する場合、`Fixed Tooltip Text`プロパティ、ツール ヒントとして使用されます。 変数の場合、ツールヒントがカスタム コードで定義します。|none|  
|メモ|この図形に関連付けられている非公式のメモ。|\<なし >|  
|初期の高さ|インチ単位で、この図形の初期の高さ。|1|  
|初期の幅|インチ単位で、この図形の初期の幅。|1.5|  
|プロパティとして公開されている塗りつぶしの色<br /><br /> 公開された塗りつぶしのグラデーション モード<br /><br /> アウトラインの色をプロパティとして公開<br /><br /> 輪郭の実線/点線スタイルをプロパティとして公開<br /><br /> アウトラインの太さのプロパティとして公開されています。<br /><br /> テキストの色を公開します。|場合`True`図形の規定されたプロパティを設定できます。 この設定は、シェイプの定義を右クリックし、クリックして**公開追加**します。|False|  
|説明|生成されたデザイナーを文書化するために使用します。|\<なし >|  
|表示名|この図形に生成されたデザイナーに表示される名前です。|\<なし >|  
|固定ツール ヒント テキスト|固定のツールヒントに使用されるテキスト。|\<なし >|  
|ヘルプ キーワード|この図形の F1 ヘルプのインデックスを作成するために使用するキーワードです。|\<なし >|  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



