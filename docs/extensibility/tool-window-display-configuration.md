---
title: "ツール ウィンドウの表示の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9478ffb6ffc1fcd2204065ff4fb7cb113ab88ba4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-window-display-configuration"></a>ツール ウィンドウの表示構成
VSPackage でツール ウィンドウ、既定の位置、サイズ、ドッキング スタイル、およびその他の表示/非表示情報を登録するときは、省略可能な値で指定されます。 ツール ウィンドウの登録の詳細については、次を参照してください[レジストリ内のツール ウィンドウ。](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>ウィンドウの表示情報  
 ツール ウィンドウの基本的な表示の構成は、最大&6; 個の省略可能な値に格納されます。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|名前|REG_SZ|「短い名前ここに挿入」|ツール ウィンドウを説明する短い名前です。 レジストリ内の参照でのみ使用されます。|  
|Float|REG_SZ|"X1 Y1, X2 Y2"|次の&4; つのコンマ区切りの値。 X1、Y1、ツール ウィンドウの左上隅の座標。 X2、Y2、右下隅の座標。 すべての値は、画面座標でです。|  
|スタイル|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> 「リンク」<br /><br /> 「タブ」<br /><br /> "AlwaysFloat"|最初に指定するキーワードは、ツール ウィンドウの状態を表示します。<br /><br /> "MDI"= MDI ウィンドウとドッキングします。<br /><br /> "Float"浮動 = です。<br /><br /> 「リンク」= (ウィンドウのエントリで指定された) 別のウィンドウでリンクされています。<br /><br /> 「タブ」= 別のツール ウィンドウで結合します。<br /><br /> "AlwaysFloat"= ドッキングことはできません。<br /><br /> 詳細については、下の [コメント] セクションを参照してください。|  
|ウィンドウ|REG_SZ|*\<GUID >*|ツール ウィンドウのリンクやタブ付きウィンドウの GUID です。 GUID は、独自のウィンドウのいずれかまたはで windows のいずれかに属することが、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE です。|  
|[方向]|REG_SZ|"Left"<br /><br /> "Right"<br /><br /> Top<br /><br /> 「下部にある」|下の [コメント] セクションを参照してください。|  
|DontForceCreate|REG_DWORD|0 または 1|このエントリが存在し、その値が&0; でない場合は、ウィンドウが読み込まれますが、すぐに表示されます。|  
  
### <a name="comments"></a>コメント  
 印刷の向きエントリは、タイトル バーをダブルクリックしたときにツール ウィンドウがドッキング位置を定義します。 ウィンドウのエントリで指定されたウィンドウの相対位置では。 スタイルのエントリは、「リンクされた」に設定されている場合、"Left"、"Right"、"Top"または「下部にある」は、印刷の向きエントリがあることができます。 場合はスタイル エントリは、「タブ」で、印刷の向きのエントリ「そのまま」または"Right"があり、このタブを追加する場所を指定します。 スタイルのエントリが"Float"場合は、ツール ウィンドウは最初に寄せて配置します。 タイトル バーがダブルクリックされたとき、印刷の向きとウィンドウのエントリを適用してウィンドウが「タブ」スタイルを使用します。 スタイルのエントリが"AlwaysFloat"の場合は、ツール ウィンドウをドッキングすることはできません。 スタイルのエントリが"MDI"の場合は、ツール ウィンドウが MDI 領域にリンクされているし、ウィンドウのエントリは無視されます。  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>ツール ウィンドウの表示  
 オプションの表示/非表示のサブキーの値では、ツール ウィンドウの可視性の設定によって決まります。 値の名前は、ウィンドウの表示/非表示を必要とするコマンドの Guid の格納に使用されます。 コマンドを実行すると場合、IDE は、ツール ウィンドウが作成され、表示されることを保証します。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|(既定)|REG_SZ|なし|空のままにします。|  
|*\<GUID >*|REG_DWORD または REG_SZ|0 またはわかりやすい文字列です。|省略可能です。 エントリの名前は、可視性を必要とするコマンドの GUID である必要があります。 値には、参考の構成文字列だけを保持します。 通常、値は、`reg_dword`を 0 に設定します。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPackage の基本事項](../misc/vspackage-essentials.md)
