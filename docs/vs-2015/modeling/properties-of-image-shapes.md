---
title: イメージ シェイプのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0b2de4ce9c332b5a4f54ad41e6d3af500b49956
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843484"
---
# <a name="properties-of-image-shapes"></a>イメージ シェイプのプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

イメージ シェイプを使用すると、ドメイン クラスが生成されたデザイナーで表示する方法を指定します。 設定して、イメージ シェイプの定義、`Image`クラスを定義済みのイメージ ファイルのプロパティ。 次の形式がサポートされています。  
  
- .gif  
  
- .jpg  
  
- .jpeg  
  
- .bmp  
  
- .wmf  
  
- .emf  
  
- .png  
  
  既定では、イメージ ファイルなどのデザイナーのリソース ファイル内にある、**リソース**フォルダーで、 **Dsl**プロジェクト。  
  
  詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。  
  
  イメージ シェイプには、次の表に記載されているプロパティがあります。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|[塗りつぶしの色]|この図形の塗りつぶしの色。|白|  
|塗りつぶしのグラデーション モード|この図形の塗りつぶしのグラデーション モード。|[水平方向]|  
|既定の接続ポイントします。|場合`True`図形を使用して、top、bottom、left、および右の接続は、生成されたデザイナーで参照します。|False|  
|アウトラインの色|この図形のアウトラインの色。|黒|  
|輪郭の実線/点線スタイル|(実線、ダッシュ、ドット、DashDot、DashDotDot、またはカスタム) は、この図形の輪郭の実線/点線スタイル。|[実線]|  
|外枠の太さ|この図形のアウトラインの太さです。|0.03125|  
|テキストの色|この図形に関連付けられているテキスト デコレーターに使用される色。|黒|  
|アクセス修飾子|ジオメトリ シェイプ (パブリックまたは内部) のアクセス修飾子。|Public|  
|カスタム属性|この図形から生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|  
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|  
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターは、ソース コードで提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|  
|継承修飾子|イメージ シェイプから生成されるソース コードのクラスの継承の種類について説明します (`none`、`abstract`または`sealed`)。|none|  
|基本イメージ シェイプ|この図形の基本クラス。|(なし)|  
|名前|この図形の名前。|現在の名前|  
|名前空間|この図形に関連付ける名前空間。|現在の名前空間|  
|ツールヒントの種類|ツールヒントが定義されている場所 (固定、変数、または none)。 、しの値を固定する場合、`Fixed Tooltip Text`プロパティ、ツール ヒントとして使用されます。 変数の場合、ツールヒントがカスタム コードで定義します。|none|  
|メモ|この図形に関連付けられている非公式のメモ。|\<なし >|  
|初期の高さ|インチ単位で、この図形の初期の高さ。|1|  
|初期の幅|インチ単位で、この図形の初期の幅。|1.5|  
|プロパティとして公開されている塗りつぶしの色<br /><br /> 公開された塗りつぶしのグラデーション モード<br /><br /> アウトラインの色をプロパティとして公開<br /><br /> 輪郭の実線/点線スタイルをプロパティとして公開<br /><br /> アウトラインの太さのプロパティとして公開されています。<br /><br /> テキストの色を公開します。|場合`True`図形の規定されたプロパティを設定できます。 この設定は、シェイプの定義を右クリックし、クリックして**公開追加**します。|False|  
|説明|生成されたデザイナーを文書化するために使用します。|\<なし >|  
|表示名|この図形に生成されたデザイナーに表示される名前です。|\<なし >|  
|固定のツールヒント テキスト|固定のツールヒントに使用されるテキスト。|\<なし >|  
|ヘルプ キーワード|この要素の F1 ヘルプのインデックスを作成するために使用するキーワードです。|\<なし >|  
|イメージ|この図形に使用されるイメージ ファイルへのパス。|\<なし >|  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



