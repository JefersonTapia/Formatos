<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Gestión Documental</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background-color: #f5f7fa;
            color: #2c3e50;
            line-height: 1.6;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            color: white;
            padding: 2rem 0;
            border-bottom: 3px solid #3b82f6;
        }

        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .header h1 {
            font-size: 2rem;
            font-weight: 500;
            letter-spacing: -0.5px;
            margin-bottom: 0.5rem;
        }

        .header p {
            color: #94a3b8;
            font-size: 1rem;
        }

        .stats {
            margin-top: 1rem;
            display: inline-block;
            padding: 0.5rem 1.5rem;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 100px;
            font-size: 0.9rem;
            color: #e2e8f0;
        }

        .stats span {
            color: #3b82f6;
            font-weight: 600;
            margin-right: 0.5rem;
        }

        /* Layout principal - ahora solo una columna */
        .main-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 2rem;
        }

        /* Panel de documentos */
        .documents-panel {
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }

        .panel-header {
            padding: 1.5rem;
            border-bottom: 1px solid #e9ecef;
        }

        .panel-header h2 {
            font-size: 1.25rem;
            font-weight: 600;
            color: #1e293b;
            margin-bottom: 0.25rem;
        }

        .panel-header p {
            color: #64748b;
            font-size: 0.9rem;
        }

        .documents-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 1.5rem;
            padding: 1.5rem;
        }

        .document-card {
            background: #f8fafc;
            border-radius: 10px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            border: 1px solid #e9ecef;
            display: flex;
            flex-direction: column;
        }

        .document-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            border-color: #3b82f6;
        }

        .document-icon {
            width: 48px;
            height: 48px;
            background: #e6f0ff;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            color: #3b82f6;
            font-size: 1.5rem;
        }

        .document-name {
            font-weight: 600;
            color: #1e293b;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
        }

        .document-meta {
            display: flex;
            gap: 1rem;
            font-size: 0.85rem;
            color: #64748b;
            margin-bottom: 0.5rem;
        }

        .document-desc {
            font-size: 0.9rem;
            color: #475569;
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .document-actions {
            display: flex;
            gap: 0.75rem;
            margin-top: auto;
        }

        .action-btn {
            flex: 1;
            padding: 0.6rem 1rem;
            border-radius: 6px;
            font-size: 0.9rem;
            font-weight: 500;
            cursor: pointer;
            border: none;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .action-btn-view {
            background: white;
            border: 1px solid #3b82f6;
            color: #3b82f6;
        }

        .action-btn-view:hover {
            background: #e6f0ff;
        }

        .action-btn-download {
            background: #3b82f6;
            color: white;
        }

        .action-btn-download:hover {
            background: #2563eb;
        }

        /* MODAL - Ventana emergente para PDF */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.75);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(8px);
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal-window {
            background: white;
            border-radius: 16px;
            width: 95%;
            max-width: 1200px;
            height: 90vh;
            display: flex;
            flex-direction: column;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            animation: modalAppear 0.3s ease;
        }

        @keyframes modalAppear {
            from {
                opacity: 0;
                transform: scale(0.95);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .modal-header {
            padding: 1.25rem 1.5rem;
            border-bottom: 1px solid #e9ecef;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: white;
            border-radius: 16px 16px 0 0;
        }

        .modal-header-info h3 {
            font-size: 1.2rem;
            font-weight: 600;
            color: #1e293b;
            margin-bottom: 0.25rem;
        }

        .modal-header-info p {
            font-size: 0.9rem;
            color: #64748b;
        }

        .modal-header-actions {
            display: flex;
            gap: 0.75rem;
            align-items: center;
        }

        .modal-btn {
            padding: 0.5rem 1.25rem;
            border-radius: 8px;
            font-size: 0.9rem;
            font-weight: 500;
            cursor: pointer;
            border: 1px solid #e2e8f0;
            background: white;
            color: #475569;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.2s;
        }

        .modal-btn:hover {
            background: #f8fafc;
            border-color: #cbd5e1;
        }

        .modal-btn-primary {
            background: #3b82f6;
            border-color: #3b82f6;
            color: white;
        }

        .modal-btn-primary:hover {
            background: #2563eb;
        }

        .modal-close {
            width: 36px;
            height: 36px;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
            background: white;
            color: #64748b;
            font-size: 1.5rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
        }

        .modal-close:hover {
            background: #f8fafc;
            color: #1e293b;
        }

        .modal-content {
            flex: 1;
            overflow: hidden;
            background: #f8fafc;
            border-radius: 0 0 16px 16px;
        }

        .modal-content iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Modal de éxito (descarga) */
        .success-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1100;
        }

        .success-modal.active {
            display: flex;
        }

        .success-content {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
            animation: modalAppear 0.3s ease;
        }

        .success-icon {
            width: 64px;
            height: 64px;
            background: #10b981;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1.5rem;
            color: white;
            font-size: 2rem;
        }

        .success-content h3 {
            color: #1e293b;
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }

        .success-content p {
            color: #64748b;
            margin-bottom: 1.5rem;
        }

        .success-btn {
            padding: 0.75rem 2rem;
            background: #3b82f6;
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            transition: background 0.2s;
        }

        .success-btn:hover {
            background: #2563eb;
        }

        /* Loading spinner */
        .loading {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
        }

        .spinner {
            width: 48px;
            height: 48px;
            border: 4px solid #e2e8f0;
            border-top-color: #3b82f6;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
            margin-bottom: 1rem;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content,
            .main-container {
                padding: 0 1rem;
            }
            
            .documents-grid {
                grid-template-columns: 1fr;
            }
            
            .modal-window {
                width: 100%;
                height: 100%;
                border-radius: 0;
            }
            
            .modal-header {
                border-radius: 0;
            }
            
            .modal-content {
                border-radius: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="header-content">
            <h1>Sistema de Gestión Documental</h1>
            <p>Repositorio corporativo de documentos institucionales</p>
            <div class="stats">
                <span id="documentCount">6</span> documentos disponibles
            </div>
        </div>
    </header>

    <!-- Contenido principal -->
    <div class="main-container">
        <!-- Panel de documentos -->
        <div class="documents-panel">
            <div class="panel-header">
                <h2>Documentos</h2>
                <p>Seleccione un documento para visualizarlo</p>
            </div>
            <div class="documents-grid" id="documentsGrid">
                <!-- Los documentos se cargarán dinámicamente -->
            </div>
        </div>
    </div>

    <!-- MODAL - Ventana emergente para PDF -->
    <div class="modal-overlay" id="pdfModal">
        <div class="modal-window">
            <div class="modal-header">
                <div class="modal-header-info">
                    <h3 id="modalTitle">Título del documento</h3>
                    <p id="modalMeta">Información del documento</p>
                </div>
                <div class="modal-header-actions">
                    <button class="modal-btn" onclick="abrirEnNuevaPestana()">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                        </svg>
                        Abrir en pestaña
                    </button>
                    <button class="modal-btn modal-btn-primary" onclick="descargarDocumentoActual()">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"/>
                        </svg>
                        Descargar
                    </button>
                    <button class="modal-close" onclick="cerrarModalPDF()">×</button>
                </div>
            </div>
            <div class="modal-content" id="modalContent">
                <!-- Aquí se cargará el PDF -->
            </div>
        </div>
    </div>

    <!-- Modal de éxito (descarga) -->
    <div class="success-modal" id="successModal">
        <div class="success-content">
            <div class="success-icon">✓</div>
            <h3>Descarga completada</h3>
            <p>El documento se ha descargado correctamente</p>
            <button class="success-btn" onclick="cerrarSuccessModal()">Aceptar</button>
        </div>
    </div>

    <script>
        // ============================================
        // CONFIGURACIÓN DE DOCUMENTOS
        // ============================================
        const documentos = [
            {
                id: 1,
                nombre: "Manual de Procedimientos 2024.pdf",
                ruta: "documentos/Dialnet-RevistasCientificasMexicanasRetosDeCalidadYVisibil-709996.pdf",
                tamaño: "2.5 MB",
                fecha: "2024-03-15",
                tipo: "PDF",
                descripcion: "Manual actualizado de procedimientos internos"
            },
            {
                id: 2,
                nombre: "Informe Anual 2023.pdf",
                ruta: "documentos/informe-2023.pdf",
                tamaño: "4.8 MB",
                fecha: "2024-02-10",
                tipo: "PDF",
                descripcion: "Informe financiero anual y resultados"
            },
            {
                id: 3,
                nombre: "Políticas de Seguridad.pdf",
                ruta: "documentos/politicas-seguridad.pdf",
                tamaño: "1.2 MB",
                fecha: "2024-01-05",
                tipo: "PDF",
                descripcion: "Políticas actualizadas de seguridad"
            },
            {
                id: 4,
                nombre: "Presentación Resultados Q1.pdf",
                ruta: "documentos/resultados-q1.pdf",
                tamaño: "3.1 MB",
                fecha: "2024-03-20",
                tipo: "PDF",
                descripcion: "Resultados del primer trimestre"
            },
            {
                id: 5,
                nombre: "Contrato Marco 2024.pdf",
                ruta: "documentos/contrato-marco.pdf",
                tamaño: "1.8 MB",
                fecha: "2024-03-01",
                tipo: "PDF",
                descripcion: "Contrato marco de servicios"
            },
            {
                id: 6,
                nombre: "Manual de Usuario Sistema.pdf",
                ruta: "documentos/manual-usuario.pdf",
                tamaño: "3.3 MB",
                fecha: "2024-03-12",
                tipo: "PDF",
                descripcion: "Manual de usuario del sistema"
            }
        ];

        let documentoActual = null;

        // Formatear fecha
        function formatearFecha(fecha) {
            const opciones = { year: 'numeric', month: 'long', day: 'numeric' };
            return new Date(fecha).toLocaleDateString('es-ES', opciones);
        }

        // Renderizar documentos en grid
        function renderizarDocumentos() {
            const grid = document.getElementById('documentsGrid');
            
            grid.innerHTML = documentos.map(doc => `
                <div class="document-card">
                    <div class="document-icon">📄</div>
                    <div class="document-name">${doc.nombre}</div>
                    <div class="document-meta">
                        <span>📄 ${doc.tipo}</span>
                        <span>📏 ${doc.tamaño}</span>
                        <span>📅 ${formatearFecha(doc.fecha)}</span>
                    </div>
                    <div class="document-desc">${doc.descripcion}</div>
                    <div class="document-actions">
                        <button class="action-btn action-btn-view" onclick="verDocumento(${doc.id})">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                            </svg>
                            Visualizar
                        </button>
                        <button class="action-btn action-btn-download" onclick="descargarDocumento(${doc.id})">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"/>
                            </svg>
                            Descargar
                        </button>
                    </div>
                </div>
            `).join('');
            
            document.getElementById('documentCount').textContent = documentos.length;
        }

        // Ver documento en modal emergente
        function verDocumento(id) {
            const doc = documentos.find(d => d.id === id);
            if (!doc) return;
            
            documentoActual = doc;
            
            // Actualizar información del modal
            document.getElementById('modalTitle').textContent = doc.nombre;
            document.getElementById('modalMeta').textContent = `${doc.tipo} • ${doc.tamaño} • ${formatearFecha(doc.fecha)}`;
            
            // Mostrar loading
            document.getElementById('modalContent').innerHTML = `
                <div class="loading">
                    <div class="spinner"></div>
                    <p style="color: #64748b;">Cargando documento...</p>
                </div>
            `;
            
            // Mostrar modal
            document.getElementById('pdfModal').classList.add('active');
            document.body.style.overflow = 'hidden';
            
            // Cargar PDF después de un pequeño delay
            setTimeout(() => {
                document.getElementById('modalContent').innerHTML = `
                    <iframe src="${doc.ruta}" title="${doc.nombre}"></iframe>
                `;
            }, 300);
        }

        // Cerrar modal de PDF
        function cerrarModalPDF() {
            document.getElementById('pdfModal').classList.remove('active');
            document.body.style.overflow = 'auto';
            documentoActual = null;
        }

        // Descargar documento
        function descargarDocumento(id) {
            const doc = documentos.find(d => d.id === id);
            if (!doc) return;
            
            fetch(doc.ruta)
                .then(response => response.blob())
                .then(blob => {
                    const url = window.URL.createObjectURL(blob);
                    const link = document.createElement('a');
                    link.href = url;
                    link.download = doc.nombre;
                    document.body.appendChild(link);
                    link.click();
                    document.body.removeChild(link);
                    window.URL.revokeObjectURL(url);
                    
                    document.getElementById('successModal').classList.add('active');
                })
                .catch(() => {
                    // Fallback: método tradicional
                    const link = document.createElement('a');
                    link.href = doc.ruta;
                    link.download = doc.nombre;
                    document.body.appendChild(link);
                    link.click();
                    document.body.removeChild(link);
                });
        }

        // Descargar documento actual (desde modal)
        function descargarDocumentoActual() {
            if (documentoActual) {
                descargarDocumento(documentoActual.id);
            }
        }

        // Abrir en nueva pestaña
        function abrirEnNuevaPestana() {
            if (documentoActual) {
                window.open(documentoActual.ruta, '_blank');
            }
        }

        // Cerrar modal de éxito
        function cerrarSuccessModal() {
            document.getElementById('successModal').classList.remove('active');
        }

        // Event listeners
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                cerrarModalPDF();
                cerrarSuccessModal();
            }
        });

        // Cerrar modal al hacer clic fuera
        document.getElementById('pdfModal').addEventListener('click', (e) => {
            if (e.target === document.getElementById('pdfModal')) {
                cerrarModalPDF();
            }
        });

        // Inicializar
        document.addEventListener('DOMContentLoaded', renderizarDocumentos);
    </script>
</body>
</html>
