---
title: ファイル格納処理および XML シリアル化のカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ee8a3b5a5510ef5b8a104e3a55ace3af9ce7d318
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592902"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>ファイル格納処理および XML シリアル化処理のカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ファイル記憶域のカスタマイズと XML シリアル化](https://docs.microsoft.com/visualstudio/modeling/customizing-file-storage-and-xml-serialization)します。  
  
ユーザーは、インスタンスを保存するときにまたは*モデル*でドメイン固有言語 (DSL) の[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、XML ファイルを作成または更新します。 ファイルは、ストア内のモデルを再作成を再読み込みすることができます。  
  
 シリアル化方式をカスタマイズするには、の設定を調整する**Xml シリアル化動作**DSL エクスプ ローラーでします。 下のノードがある**Xml シリアル化動作**のすべてのドメイン クラス、プロパティ、および関係。 リレーションシップは、そのソース クラスの下に配置されます。 図形、コネクタ、およびダイアグラムのクラスに対応するノードもあります。  
  
 高度なカスタマイズのプログラム コードを記述することもできます。  
  
> [!NOTE]
>  特定の形式でモデルを保存する場合、そのフォームから再読み込みする必要はありませんは、カスタムのシリアル化スキームではなく、モデルからの出力を生成するテキスト テンプレートの使用を検討してください。 詳細については、次を参照してください。[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)します。  
  
## <a name="model-and-diagram-files"></a>モデルと図ファイル  
 各モデルは、通常は 2 つのファイルに保存されます。  
  
-   モデル ファイルの名前はなどがあります**Model1.mydsl**します。 モデル要素およびリレーションシップとそのプロパティを格納します。 などのファイル拡張子 **.mydsl**によって決定されます、 **FileExtension**のプロパティ、**エディター** DSL 定義内のノード。  
  
-   ダイアグラム ファイルの名前はなどがあります**Model1.mydsl.diagram**します。 図形、コネクタ、およびそれらの位置、色、線の太さおよびダイアグラムの外観の他の詳細を格納します。 ユーザーを削除した場合、 ***.diagram**ファイル、モデルの重要な情報は失われません。 ダイアグラムのレイアウトだけが失われます。 モデル ファイルが開かれたときに、既定値は、図形のセットし、コネクタが作成されます。  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL のファイル拡張子を変更するには  
  
1.  DSL 定義を開きます。 DSL エクスプ ローラーで、[エディター] ノードをクリックします。  
  
2.  プロパティ ウィンドウで、編集、 **FileExtension**プロパティ。 初期が含まれていません"."ファイル名拡張子の。  
  
3.  ソリューション エクスプ ローラーでの 2 つの項目テンプレート ファイルの名前を変更**DslPackage\ProjectItemTemplates**します。 これらのファイルでは、次の形式に従って名前があります。  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>既定のシリアル化スキーム  
 このトピックの例を作成するには、次の DSL 定義が使用されました。  
  
 ![DSL 定義図&#45;ファミリ ツリー モデル](../modeling/media/familyt-person.png "FamilyT_Person")  
  
 この DSL を画面に次の外観を持つモデルを作成するために使用します。  
  
 ![ファミリ ツリー ダイアグラム、ツールボックス、およびエクスプ ローラー](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 このモデルが保存され、XML のテキスト エディターで再度開きます。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 シリアル化されたモデルについては、次の点に注意してください。  
  
-   最初の文字は小文字である点を除いて、各 XML ノードは、ドメイン クラスの名前と同じである名を持ちます。 たとえば、`familyTreeModel` と`person` です。  
  
-   ドメイン名と誕生年などのプロパティは、XML ノードの属性としてシリアル化されます。 ここでも、プロパティ名の最初の文字が小文字に変換されます。  
  
-   各リレーションシップは、リレーションシップのソース端の内側に入れ子になった XML ノードとしてシリアル化されます。 ノードでは、小文字の最初の文字が、ソース ロール プロパティと同じ名前があります。  
  
     たとえば、DSL 定義の名前はロールで**人**をソースと、 **FamilyTree**クラス。  という名前のノードで、XML で表されます`people`内で入れ子になった、`familyTreeModel`ノード。  
  
-   各埋め込みリレーションシップのターゲット エンドは、リレーションシップの下で入れ子になったノードとしてシリアル化されます。 たとえば、`people`ノードでは、いくつか含まれています`person`ノード。  
  
-   各参照リレーションシップのターゲット エンドとしてシリアル化、*モニカー*、エンコードされ、ターゲット要素への参照。  
  
     たとえば、下、`person`ノード、可能性がある、`children`リレーションシップ。 このノードには、モニカーにはなどが含まれます。  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>モニカーを理解します。  
 モニカーが使用され、モデルと図のファイルの異なる部分間の相互参照を表します。 使用することも、`.diagram`ファイルをモデル ファイル内のノードを参照してください。 これには 2 つのモニカーの形式があります。  
  
-   *Id モニカー*ターゲット要素の GUID を引用します。 例えば:  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *修飾キー モニカー*モニカー キーと呼ばれる指定されたドメイン プロパティの値によって、ターゲット要素を識別します。 ターゲット要素のモニカーのプレフィックスが付いたの埋め込みリレーションシップ ツリーで、親要素のモニカー。  
  
     次の例は、DSL がありますが、アルバムを持つクラスの名前付きの曲をドメインへの埋め込みリレーションシップをという名前のドメイン クラスから取得します。  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     ターゲット クラスにドメインのプロパティがある場合は、対象の修飾キー モニカーが使用されるオプション**モニカー キーである**に設定されている`true`で**Xml シリアル化動作**します。 例では、このオプションは、ドメイン クラスは、「アルバム」および「曲」で"Title"をという名前のドメイン プロパティに設定されます。  
  
 修飾キー モニカーはモニカーを ID よりも読みやすくします。 ユーザーによって読み取られるモデル ファイルの XML にする場合は、修飾キー モニカーの使用を検討してください。 ただし、ユーザーはモニカー キーが同じである 1 つ以上の要素を設定するは。 重複するキーには、ファイルが正しく再読み込みしない可能性があります。 そのため、修飾キー モニカーを使用して参照されているドメイン クラスを定義する場合は、重複するモニカーを含むファイルを保存してから、ユーザーを回避する方法を検討してください。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>モニカーを ID で参照されるドメイン クラスを設定するには  
  
1.  確認します**モニカー キーである**は`false`クラスとその基本クラスのすべてのドメイン プロパティにします。  
  
    1.  DSL エクスプ ローラーで、 **Xml シリアル化 Behavior\Class データ\\**_\<ドメイン クラス >_**\Element データ**します。  
  
    2.  いることを確認**モニカー キーである**は`false`のすべてのドメイン プロパティ。  
  
    3.  ドメイン クラスに基底クラスがある場合は、そのクラスの手順を繰り返します。  
  
2.  設定**Id のシリアル化** =  `true`ドメイン クラス。  
  
     このプロパティは下にあります**Xml シリアル化動作**します。  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>修飾キー モニカーによって参照されるドメイン クラスを設定するには  
  
-   設定**モニカー キーである**ドメインのプロパティの既存のドメイン クラス。 プロパティの型である必要があります`string`します。  
  
    1.  DSL エクスプ ローラーで、 **Xml シリアル化 Behavior\Class データ\\**_\<ドメイン クラス >_**\Element データ**を選び、ドメインのプロパティです。  
  
    2.  [プロパティ] ウィンドウで次のように設定します。**モニカー キーである**に`true`します。  
  
-   \- または -  
  
     新しいドメイン クラスを作成、**という名前のドメイン クラス**ツール。  
  
     このツールは、名と呼ばれるドメイン プロパティを持つ新しいクラスを作成します。 **は要素名**と**モニカー キーである**にこのドメイン プロパティのプロパティが初期化されます`true`します。  
  
-   \- または -  
  
     モニカー キー プロパティを持つ別のクラスに、ドメイン クラスから継承リレーションシップを作成します。  
  
### <a name="avoiding-duplicate-monikers"></a>重複するモニカーを回避します。  
 修飾キー モニカーを使用する場合は、ユーザーのモデル内の 2 つの要素がキー プロパティに同じ値を持つことができます。 たとえば、DSL にクラス プロパティ名を持つユーザーがある場合は、ユーザーは同じである 2 つの要素の名前を設定します。 モデルになりますがファイルに保存すると、これは再読み込みされません正しくします。  
  
 このような状況を避けるために役立ついくつかの方法はあります。  
  
-   設定**は要素名** =  `true`キーのドメイン プロパティ。 DSL 定義図のドメイン プロパティを選択し、[プロパティ] ウィンドウで、値を設定します。  
  
     ユーザーは、クラスの新しいインスタンスを作成し、この値とドメイン プロパティは、別の値を自動的に割り当てられます。 既定の動作は、クラス名の末尾に数値を追加します。 これは、ユーザーから、重複する名前を変更するが、ユーザーが、モデルを保存する前に、値を設定しない場合の場合は、できます。  
  
-   DSL の検証を有効にします。 DSL エクスプ ローラーで、エディターを選択し、設定、**を使用しています.** プロパティ`true`します。  
  
     あいまいさをチェックする検証を自動的に生成されたメソッドが存在します。 メソッドが含まれる、`Load`検証カテゴリ。 これにより、ファイルを再度開くできない可能性があります、そのユーザーを警告はことを確認します。  
  
     詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。  
  
### <a name="moniker-paths-and-qualifiers"></a>モニカーのパスと修飾子  
 修飾キー モニカーは、モニカー キーで終了し、埋め込みツリー内の親のモニカーが付いています。 たとえば、アルバムのモニカーとします。  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 そのアルバムの曲のいずれかの可能性があります。  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 ただし、アルバムは、ID によって参照される場合、モニカーをとおりのようになります  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 GUID は一意であるためには決して付ける必要がその親のモニカーでに注意してください。  
  
 特定のドメイン プロパティには、モデル内の一意の値を必ずことがわかっている場合を設定できます**がモニカー修飾子**に`true`プロパティ。 親のモニカーを使用せず、修飾子として使用されるようになります。 たとえば、次の両方を設定する**がモニカー修飾子**と**モニカー キーである**アルバム クラスの Title ドメイン プロパティのモデルの名前または識別子で使用されていないモニカーのアルバムとその埋め込み子:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>XML の構造をカスタマイズします。  
 次のカスタマイズをするためには、展開、 **Xml シリアル化動作**DSL エクスプ ローラーでノード。 ドメイン クラス、プロパティとこのクラスをソースとは関係の一覧を表示する要素のデータ ノードを展開します。 リレーションシップを選択し、[プロパティ] ウィンドウでオプションを調整します。  
  
-   設定**要素の省略**にターゲット要素の一覧だけを残して、ソース ロール ノードを省略する場合は true。 ソースとターゲットのクラス間で複数のリレーションシップがある場合は、このオプションを設定する必要があります。  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   設定**完全な形式を使用して**リレーションシップ インスタンスを表すノードにターゲット ノードを埋め込む。 このオプションは、ドメイン リレーションシップにドメインのプロパティを追加すると、自動的に設定されます。  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   設定**表現** = **要素**ドメイン プロパティが属性値としての代わりに要素として保存されます。  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   属性とのリレーションシップがシリアル化順序を変更するには、下にある要素のデータ項目を右クリックし、使用、**上へ移動**または**下へ移動**メニュー コマンド。  
  
## <a name="major-customization-using-program-code"></a>プログラム コードを使用して主なカスタマイズ  
 シリアル化アルゴリズムの一部または全体を置き換えることができます。  
  
 内のコードを学習することをお勧めします。 **Dsl\Generated Code\Serializer.cs**と**SerializationHelper.cs**します。  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>特定のクラスのシリアル化をカスタマイズするには  
  
1.  設定**カスタム**そのクラスの下のノードに**Xml シリアル化動作**します。  
  
2.  すべてのテンプレートの変換、ソリューションをビルドし、コンパイル エラーの発生を調査します。 各エラーの近くのコメントには、どのようなコードを入力するについて説明します。  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>モデル全体の独自のシリアル化を提供するには  
  
1.  Dsl\GeneratedCode\SerializationHelper.cs でメソッドをオーバーライドします。  
  
## <a name="options-in-xml-serialization-behavior"></a>Xml シリアル化動作のオプション  
 DSL エクスプ ローラーでは、Xml シリアル化動作ノードには、各ドメイン クラス、リレーションシップ、図形、コネクタと図のクラスの子ノードが含まれています。 各ノードの下で、プロパティとその要素をソースとの関係の一覧です。 リレーションシップは、独自の右にあると、ソース クラスの下の両方に表されます。  
  
 次の表では、DSL 定義のこのセクションで設定できるオプションをまとめたものです。 各ケースでは、DSL エクスプ ローラーで要素を選択し、[プロパティ] ウィンドウで、オプションを設定します。  
  
### <a name="xml-class-data"></a>Xml クラス データ  
 DSL エクスプ ローラーでこれらの要素にある**Xml シリアル化 Behavior\Class データ**します。  
  
|||  
|-|-|  
|プロパティ|説明|  
|カスタム要素スキーマがあります。|True の場合は、ドメイン クラスにカスタム要素スキーマがあることを示します。|  
|カスタムします。|これを設定**True**このドメイン クラスの独自のシリアル化および逆シリアル化コードを記述するかどうか。<br /><br /> ソリューションをビルドし、詳細な手順を検出するエラーを調査します。|  
|ドメイン クラス|ドメイン クラスがこのクラスのデータ ノードが適用されます。 読み取り専用。|  
|要素名|このクラスの要素の Xml ノードの名前。 既定値は、ドメインのクラス名は小文字です。|  
|モニカー属性名|参照を格納するモニカー要素で使用される属性の名前です。 空白の場合は、キー プロパティまたは id の名前が使用されます。<br /><br /> この例では、"name"することをお勧めします。  `<personMoniker name="/Mike Nash"/>`|  
|モニカー要素名|このクラスの要素を参照するモニカーを使用する xml 要素の名前です。<br /><br /> 既定値は、"Moniker"サフィックスが付いて、クラス名の小文字版です。 たとえば、`personMoniker` のようにします。|  
|モニカーの型名|このクラスの要素に対するモニカー用に生成される xsd 型の名前。 XSD が**Dsl\Generated コード\\\*Schema.xsd**|  
|Id をシリアル化します。|True の場合は、ファイルに要素 GUID にはが含まれます。 これがマークされているプロパティが存在しない場合は true である必要があります**モニカー キーである**DSL がこのクラスに参照リレーションシップを定義します。|  
|型の名前|指定したドメイン クラスから xsd で生成された xml 型の名前です。|  
|メモ|この要素に関連付けられた非公式のメモ|  
  
### <a name="xml-property-data"></a>Xml プロパティ データ  
 Xml プロパティの各ノードはクラス ノードの下にあります。  
  
|||  
|-|-|  
|プロパティ|説明|  
|ドメイン プロパティ|Xml シリアル化の構成データが適用されるプロパティ。 読み取り専用。|  
|モニカー キーです。|True の場合、このプロパティは、このドメイン クラスのインスタンスを参照するモニカーを作成するためのキーとして使用されます。|  
|モニカー修飾子は、します。|True の場合、モニカーの修飾子を作成するため、プロパティが使用されます。 False の場合、SerializeId がこのドメイン クラスの場合は true でない場合は、モニカーが埋め込みツリーの親要素のモニカーで修飾されます。|  
|表現|属性、プロパティは xml 属性としてシリアル化する場合かどうか、要素は、要素としてシリアル化かどうか、無視することはできませんをシリアル化します。|  
|Xml 名|Xml 属性またはプロパティを表す要素に使用される名前。 既定では、これは、ドメインのプロパティ名の小文字版です。|  
|メモ|この要素に関連付けられた非公式のメモ|  
  
### <a name="xml-role-data"></a>ロールの Xml データ  
 ロールのデータ ノードはソース クラスのノードの下にあります。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|カスタム モニカー|これを生成して、このリレーションシップを走査するモニカーを解決するための独自のコードを提供する場合は true に設定します。<br /><br /> 詳細な手順については、ソリューションをビルドし、エラー メッセージをダブルクリックします。|  
|ドメイン リレーションシップ|これらのオプションを適用するリレーションシップを指定します。 読み取り専用。|  
|要素を省略します。|True の場合は、ソース ロールに対応する XML ノードがスキーマから省略されます。<br /><br /> ソースとターゲットのクラス間で複数のリレーションシップがある場合、このロールのノードは 2 つのリレーションシップに属しているリンクによって区別されます。 そのためことはないオプションを設定するこのここでお勧めします。|  
|ロール要素名|ソース ロールから派生する XML 要素の名前を指定します。 既定値は、ロールのプロパティ名です。|  
|完全な形式を使用します。|True の場合は、各ターゲット要素またはモニカーがリレーションシップを表す XML ノードで囲まれます。 これは、リレーションシップでは、独自のドメイン プロパティの場合は true に設定する必要があります。|  
  
## <a name="see-also"></a>関連項目  
 [移動して、プログラム コードでモデルを更新しています](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)



