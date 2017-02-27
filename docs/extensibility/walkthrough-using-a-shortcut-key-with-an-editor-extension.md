---
title: "チュートリアル: エディター拡張機能とショートカット キーを使用します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] が新たなキーストロークをコマンドにリンクします。"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# チュートリアル: エディター拡張機能とショートカット キーを使用します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディター拡張機能で、ショートカット キーに対応することができます。 次のチュートリアルでは、ショートカット キーを使用して、テキスト ビューをビューの表示要素を追加する方法を説明します。 このチュートリアルは、ビューポート adornment エディター テンプレートに基づいておりを使用して、表示要素を追加することができます、\+ 文字です。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## Managed Extensibility Framework \(MEF\) プロジェクトの作成  
  
1.  C\# の場合は、VSIX プロジェクトを作成します。 \(で、 **新しいプロジェクト** ダイアログで、 **Visual c\#\/機能拡張**, 、し **VSIX プロジェクト**.\) ソリューションの名前 `KeyBindingTest`します。  
  
2.  エディターのテキストの表示要素項目テンプレートをプロジェクトに追加し、名前 `KeyBindingTest`します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  次の参照を追加し、設定 **CopyLocal** に `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 KeyBindingTest クラス ファイルでは、PurpleCornerBox にクラス名を変更します。 その他の適切な変更を加える左マージンに表示される、light bulb を使用します。 コンス トラクター内から表示要素のレイヤーの名前を変更する **KeyBindingTest** に **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## コマンドのフィルターを定義します。  
 コマンドのフィルターの実装は、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, 、表示要素をインスタンス化して、コマンドを処理します。  
  
1.  クラス ファイルを追加し、名前 `KeyBindingCommandFilter`します。  
  
2.  次の using ステートメントを追加します。  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  KeyBindingCommandFilter という名前のクラスを継承する必要があります <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  コマンドのチェーン、およびコマンドのフィルターは既に追加されているかどうかを表すフラグでプライベート フィールド、テキスト ビューを次のコマンドを追加します。  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  テキスト ビューを設定するコンス トラクターを追加します。  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  実装、 `QueryStatus()` メソッドを次のようにします。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  実装、 `Exec()` 場合は、it がビューに紫色のボックスを追加するためのメソッドを \+ 文字を入力します。  
  
    ```c#  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## コマンドのフィルターを追加します。  
 Adornment プロバイダーは、テキスト ビューにコマンドのフィルターを追加する必要があります。 この例では、プロバイダーを実装して <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> テキスト ビューの作成イベントをリッスンするようにします。 この表示要素プロバイダーでは、表示要素の Z オーダーを定義する表示要素のレイヤーもエクスポートします。  
  
1.  KeyBindingTestTextViewCreationListener ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  レイヤーの表示要素の定義でから AdornmentLayer の名前変更 **KeyBindingTest** に **PurpleCornerBox**します。  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  テキスト ビュー アダプターを取得するには、インポートする必要があります、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>です。  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  変更、 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> メソッドを追加、 `KeyBindingCommandFilter`です。  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` ハンドラーは、テキスト ビュー アダプターを取得し、コマンドのフィルターを追加します。  
  
    ```c#  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## 表示要素を行うすべての行に表示されます  
 すべての文字で表示されていた元の表示要素の ' a' のテキスト ファイルです。 行にのみ表示要素が追加されるので、'\+' の文字への応答の表示要素を追加するコードを変更したことで、'\+' が型指定されています。 もう一度表示要素を表示、表示要素のコードを変更できますすべて 'a' です。  
  
 KeyBindingTest.cs ファイルでは、'a' 文字の装飾にビューのすべての行を反復処理する CreateVisuals\(\) メソッドを変更します。  
  
```c#  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## コードのビルドとテスト  
  
1.  KeyBindingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
2.  作成するか、テキスト ファイルを開きます。 文字を含む一部の単語の入力 'a' と入力テキスト ビューの任意の場所にある \+ です。  
  
     紫色の四角形は、ファイル内のすべての 'a' 文字に表示されます。