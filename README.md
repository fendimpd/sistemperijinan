<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Perijinan</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css">
    <style>
        :root {
            --primary-color: #1a73e8;
            --primary-dark: #1557b0;
            --primary-light: #d2e3fc;
            --secondary-color: #5f6368;
            --success-color: #0f9d58;
            --warning-color: #f9ab00;
            --danger-color: #ea4335;
            --light-color: #f8f9fa;
            --white-color: #ffffff;
            --gray-color: #f1f3f4;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--light-color);
            color: #202124;
            margin: 0;
            padding: 0;
        }
        
        /* Navigation */
        .navbar-custom {
            background-color: var(--primary-color);
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            padding: 10px 0;
        }
        
        .navbar-custom .navbar-brand {
            color: var(--white-color);
            font-weight: 600;
            font-size: 1.5rem;
        }
        
        .navbar-custom .nav-link {
            color: rgba(255,255,255,0.8);
            padding: 8px 16px;
            margin: 0 5px;
            border-radius: 5px;
            transition: all 0.3s;
        }
        
        .navbar-custom .nav-link:hover,
        .navbar-custom .nav-link.active {
            background-color: rgba(255,255,255,0.2);
            color: var(--white-color);
        }
        
        .navbar-custom .export-btn {
            background-color: rgba(255,255,255,0.2);
            border: 1px solid rgba(255,255,255,0.3);
            color: var(--white-color);
            padding: 6px 12px;
            border-radius: 5px;
            transition: all 0.3s;
        }
        
        .navbar-custom .export-btn:hover {
            background-color: rgba(255,255,255,0.3);
            border-color: rgba(255,255,255,0.5);
            color: var(--white-color);
        }
        
        /* Main Content - Full Width */
        .main-content {
            width: 100%;
            padding: 20px;
            max-width: 100%;
        }
        
        @media (min-width: 1200px) {
            .main-content {
                padding: 30px;
            }
        }
        
        /* Page Content */
        .page-content {
            display: none;
        }
        
        .page-content.active {
            display: block;
        }
        
        /* Card Styles */
        .card {
            border-radius: 8px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
            margin-bottom: 20px;
            border: none;
        }
        
        .card-header {
            background-color: var(--white-color);
            border-bottom: 1px solid #e0e0e0;
            font-weight: 500;
            padding: 15px 20px;
            color: var(--secondary-color);
        }
        
        .notification-card {
            background-color: var(--white-color);
            border-left: 4px solid var(--warning-color);
        }
        
        /* Stat Cards */
        .stat-card {
            border-radius: 8px;
            padding: 15px;
            color: var(--white-color);
            margin-bottom: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
            min-height: 100px;
        }
        
        .stat-card h5 {
            font-size: 0.9rem;
            margin-bottom: 10px;
            opacity: 0.9;
        }
        
        .stat-card h2 {
            font-size: 1.8rem;
            margin-bottom: 0;
            font-weight: 600;
        }
        
        .stat-card.total {
            background-color: var(--primary-color);
        }
        
        .stat-card.active {
            background-color: var(--success-color);
        }
        
        .stat-card.expired {
            background-color: var(--danger-color);
        }
        
        .stat-card.expiring {
            background-color: var(--warning-color);
        }
        
        /* Buttons */
        .btn-primary {
            background-color: var(--primary-color);
            border: none;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        .btn-sm {
            padding: 0.25rem 0.5rem;
            font-size: 0.75rem;
        }
        
        .btn-xs {
            padding: 0.125rem 0.25rem;
            font-size: 0.7rem;
        }
        
        /* Table Styles */
        .table th {
            background-color: var(--gray-color);
            font-weight: 500;
            color: var(--secondary-color);
        }
        
        .table-responsive {
            overflow-x: auto;
        }
        
        /* Status Badge */
        .status-badge {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }
        
        .status-active {
            background-color: rgba(15, 157, 88, 0.15);
            color: var(--success-color);
        }
        
        .status-expired {
            background-color: rgba(234, 67, 53, 0.15);
            color: var(--danger-color);
        }
        
        .status-warning {
            background-color: rgba(249, 171, 0, 0.15);
            color: var(--warning-color);
        }
        
        /* Modal Styles */
        .modal-header {
            background-color: var(--primary-color);
            color: var(--white-color);
        }
        
        /* Form Styles */
        .form-control:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.2rem rgba(26, 115, 232, 0.25);
        }
        
        /* Settings Section */
        .settings-section {
            margin-bottom: 30px;
        }
        
        .settings-section h5 {
            margin-bottom: 15px;
            color: var(--secondary-color);
            border-bottom: 1px solid #e0e0e0;
            padding-bottom: 10px;
        }
        
        /* Toast */
        .toast-container {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1050;
        }
        
        .custom-toast {
            min-width: 300px;
        }
        
        /* Filter Container */
        .filter-container {
            background-color: var(--white-color);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
        }
        
        /* Expiring Card */
        .expiring-card {
            background-color: var(--white-color);
            border-left: 4px solid var(--warning-color);
            margin-bottom: 10px;
            padding: 15px;
            border-radius: 4px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
        }
        
        .expiring-card .card-body {
            padding: 0;
        }
        
        .expiring-card .days-left {
            font-weight: 600;
            color: var(--warning-color);
        }
        
        /* Action Buttons */
        .action-buttons {
            display: flex;
            gap: 5px;
            flex-wrap: wrap;
        }
        
        .action-buttons .btn {
            display: flex;
            align-items: center;
            justify-content: center;
            min-width: 80px;
        }
        
        @media (max-width: 576px) {
            .action-buttons {
                flex-direction: column;
                gap: 3px;
            }
            
            .action-buttons .btn {
                width: 100%;
            }
        }
        
        /* Responsive adjustments for larger screens */
        @media (min-width: 1400px) {
            .container-fluid, .container-lg, .container-md, .container-sm, .container-xl {
                max-width: 100%;
            }
        }
        
        @media (min-width: 1200px) {
            .stat-card {
                min-height: 120px;
            }
            
            .stat-card h2 {
                font-size: 2.2rem;
            }
            
            .table {
                font-size: 1rem;
            }
        }
        
        /* Navbar adjustments for export button */
        @media (max-width: 768px) {
            .navbar-custom .export-btn {
                margin-top: 10px;
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar navbar-expand-lg navbar-custom">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
                <i class="bi bi-file-earmark-text me-2"></i>Sistem Perijinan
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#" data-page="dashboard">
                            <i class="bi bi-speedometer2 me-1"></i> Dashboard
                        </a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" data-page="settings">
                            <i class="bi bi-gear me-1"></i> Pengaturan
                        </a>
                    </li>
                </ul>
                <button class="btn export-btn" id="export-btn">
                    <i class="bi bi-file-earmark-excel me-1"></i> Export Excel
                </button>
            </div>
        </div>
    </nav>
    
    <!-- Main Content -->
    <div class="main-content">
        <!-- Dashboard Page -->
        <div id="dashboard-page" class="page-content active">
            <!-- Statistics Cards -->
            <div class="row mb-4">
                <div class="col-md-6 col-lg-3">
                    <div class="stat-card total">
                        <h5>Total Perijinan</h5>
                        <h2 id="total-permissions">0</h2>
                    </div>
                </div>
                <div class="col-md-6 col-lg-3">
                    <div class="stat-card active">
                        <h5>Ijin Aktif</h5>
                        <h2 id="active-permissions">0</h2>
                    </div>
                </div>
                <div class="col-md-6 col-lg-3">
                    <div class="stat-card expiring">
                        <h5>Akan Kadaluarsa</h5>
                        <h2 id="expiring-permissions">0</h2>
                    </div>
                </div>
                <div class="col-md-6 col-lg-3">
                    <div class="stat-card expired">
                        <h5>Ijin Kadaluarsa</h5>
                        <h2 id="expired-permissions">0</h2>
                    </div>
                </div>
            </div>
            
            <!-- Expiring Permissions -->
            <div class="card notification-card mb-4">
                <div class="card-header d-flex justify-content-between align-items-center">
                    <h5 class="mb-0">Ijin Akan Kadaluarsa</h5>
                    <span class="badge bg-warning text-dark" id="notification-count">0</span>
                </div>
                <div class="card-body">
                    <div id="expiring-permissions-list">
                        <p class="text-muted">Tidak ada ijin yang akan kadaluarsa dalam <span id="notification-days">60</span> hari ke depan.</p>
                    </div>
                </div>
            </div>
            
            <!-- Filter Container -->
            <div class="filter-container">
                <div class="row g-3">
                    <div class="col-md-4">
                        <div class="input-group">
                            <span class="input-group-text"><i class="bi bi-search"></i></span>
                            <input type="text" class="form-control" id="search-input" placeholder="Cari perijinan...">
                        </div>
                    </div>
                    <div class="col-md-2">
                        <select class="form-select" id="filter-category">
                            <option value="">Semua Kategori</option>
                            <option value="Ijin Klinik">Ijin Klinik</option>
                            <option value="Ijin Rumah Sakit">Ijin Rumah Sakit</option>
                            <option value="Lainnya">Lainnya</option>
                        </select>
                    </div>
                    <div class="col-md-2">
                        <select class="form-select" id="filter-status">
                            <option value="">Semua Status</option>
                            <option value="Aktif">Aktif</option>
                            <option value="Kadaluarsa">Kadaluarsa</option>
                            <option value="Akan Kadaluarsa">Akan Kadaluarsa</option>
                        </select>
                    </div>
                    <div class="col-md-2">
                        <select class="form-select" id="sort-by">
                            <option value="">Urutkan</option>
                            <option value="category">Jenis Ijin</option>
                            <option value="endDate">Tanggal Akhir</option>
                            <option value="status">Status</option>
                        </select>
                    </div>
                    <div class="col-md-2">
                        <button class="btn btn-outline-secondary w-100" id="reset-filter">
                            <i class="bi bi-arrow-clockwise me-1"></i> Reset
                        </button>
                    </div>
                </div>
            </div>
            
            <!-- Permissions Table -->
            <div class="card">
                <div class="card-header d-flex justify-content-between align-items-center">
                    <h5 class="mb-0">Data Perijinan</h5>
                    <button class="btn btn-primary btn-sm" data-bs-toggle="modal" data-bs-target="#addPermissionModal">
                        <i class="bi bi-plus-circle me-1"></i> Tambah Ijin
                    </button>
                </div>
                <div class="card-body">
                    <div class="table-responsive">
                        <table class="table table-hover" id="permissions-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Jenis Ijin</th>
                                    <th>Deskripsi</th>
                                    <th>Tanggal Terbit</th>
                                    <th>Tanggal Akhir</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="permissions-tbody">
                                <!-- Data will be inserted here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Settings Page -->
        <div id="settings-page" class="page-content">
            <h2 class="mb-4">Pengaturan</h2>
            
            <!-- Jenis Ijin Section -->
            <div class="card mb-4">
                <div class="card-header">
                    <h5 class="mb-0">Kelola Jenis Ijin</h5>
                </div>
                <div class="card-body">
                    <div class="mb-3">
                        <div class="input-group">
                            <input type="text" class="form-control" id="new-permission-type" placeholder="Tambah jenis ijin baru">
                            <button class="btn btn-primary" id="add-permission-type">Tambah</button>
                        </div>
                    </div>
                    <div class="table-responsive">
                        <table class="table" id="permission-types-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Jenis Ijin</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="permission-types-tbody">
                                <!-- Data will be inserted here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Notifikasi Section -->
            <div class="card">
                <div class="card-header">
                    <h5 class="mb-0">Pengaturan Notifikasi</h5>
                </div>
                <div class="card-body">
                    <div class="mb-3">
                        <label for="notification-days-input" class="form-label">Notifikasi Sebelum Ijin Kadaluarsa (hari)</label>
                        <div class="input-group">
                            <input type="number" class="form-control" id="notification-days-input" min="1" max="365" value="60">
                            <button class="btn btn-primary" id="save-notification-settings">Simpan</button>
                        </div>
                        <div class="form-text">Sistem akan menampilkan notifikasi untuk ijin yang akan kadaluarsa dalam jumlah hari yang ditentukan.</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Add Permission Modal -->
    <div class="modal fade" id="addPermissionModal" tabindex="-1" aria-labelledby="addPermissionModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="addPermissionModalLabel">Tambah Ijin Baru</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="add-permission-form">
                        <div class="mb-3">
                            <label for="permission-type" class="form-label">Jenis Ijin</label>
                            <select class="form-select" id="permission-type" required="">
                                <option value="" selected="" disabled="">Pilih jenis ijin</option>
                                <option value="Ijin Klinik">Ijin Klinik</option>
                                <option value="Ijin Rumah Sakit">Ijin Rumah Sakit</option>
                                <option value="Lainnya">Lainnya</option>
                            </select>
                        </div>
                        <div class="mb-3" id="custom-permission-type-group" style="display: none;">
                            <label for="custom-permission-type" class="form-label">Jenis Ijin Lainnya</label>
                            <input type="text" class="form-control" id="custom-permission-type" placeholder="Masukkan jenis ijin">
                        </div>
                        <div class="mb-3">
                            <label for="permission-description" class="form-label">Deskripsi Ijin</label>
                            <textarea class="form-control" id="permission-description" rows="3" required=""></textarea>
                        </div>
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="issue-date" class="form-label">Tanggal Terbit</label>
                                <input type="date" class="form-control" id="issue-date" required="">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="expiry-date" class="form-label">Tanggal Akhir</label>
                                <input type="date" class="form-control" id="expiry-date" required="">
                            </div>
                        </div>
                    </form>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-primary" id="save-permission">Simpan</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Edit Permission Modal -->
    <div class="modal fade" id="editPermissionModal" tabindex="-1" aria-labelledby="editPermissionModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="editPermissionModalLabel">Edit Ijin</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="edit-permission-form">
                        <input type="hidden" id="edit-permission-id">
                        <div class="mb-3">
                            <label for="edit-permission-type" class="form-label">Jenis Ijin</label>
                            <select class="form-select" id="edit-permission-type" required="">
                                <option value="" selected="" disabled="">Pilih jenis ijin</option>
                                <option value="Ijin Klinik">Ijin Klinik</option>
                                <option value="Ijin Rumah Sakit">Ijin Rumah Sakit</option>
                                <option value="Lainnya">Lainnya</option>
                            </select>
                        </div>
                        <div class="mb-3" id="edit-custom-permission-type-group" style="display: none;">
                            <label for="edit-custom-permission-type" class="form-label">Jenis Ijin Lainnya</label>
                            <input type="text" class="form-control" id="edit-custom-permission-type" placeholder="Masukkan jenis ijin">
                        </div>
                        <div class="mb-3">
                            <label for="edit-permission-description" class="form-label">Deskripsi Ijin</label>
                            <textarea class="form-control" id="edit-permission-description" rows="3" required=""></textarea>
                        </div>
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="edit-issue-date" class="form-label">Tanggal Terbit</label>
                                <input type="date" class="form-control" id="edit-issue-date" required="">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="edit-expiry-date" class="form-label">Tanggal Akhir</label>
                                <input type="date" class="form-control" id="edit-expiry-date" required="">
                            </div>
                        </div>
                    </form>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-primary" id="update-permission">Perbarui</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Update Permission Modal -->
    <div class="modal fade" id="updatePermissionModal" tabindex="-1" aria-labelledby="updatePermissionModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="updatePermissionModalLabel">Perbarui Ijin</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="update-permission-form">
                        <input type="hidden" id="update-permission-id">
                        <div class="mb-3">
                            <label for="update-expiry-date" class="form-label">Tanggal Akhir Baru</label>
                            <input type="date" class="form-control" id="update-expiry-date" required="">
                        </div>
                        <div class="mb-3">
                            <label for="update-note" class="form-label">Catatan (Opsional)</label>
                            <textarea class="form-control" id="update-note" rows="3"></textarea>
                        </div>
                    </form>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-primary" id="save-update-permission">Simpan</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Delete Confirmation Modal -->
    <div class="modal fade" id="deleteConfirmationModal" tabindex="-1" aria-labelledby="deleteConfirmationModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="deleteConfirmationModalLabel">Konfirmasi Hapus</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <p>Apakah Anda yakin ingin menghapus ijin ini?</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-danger" id="confirm-delete">Hapus</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Permission History Modal -->
    <div class="modal fade" id="permissionHistoryModal" tabindex="-1" aria-labelledby="permissionHistoryModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="permissionHistoryModalLabel">Riwayat Perijinan</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="table-responsive">
                        <table class="table" id="permission-history-table">
                            <thead>
                                <tr>
                                    <th>Tanggal Update</th>
                                    <th>Tanggal Akhir Baru</th>
                                    <th>Catatan</th>
                                </tr>
                            </thead>
                            <tbody id="permission-history-tbody">
                                <!-- Data will be inserted here -->
                            </tbody>
                        </table>
                    </div>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Tutup</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Toast Container -->
    <div class="toast-container"></div>
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
    <script>
        // Data storage
        let permissions = [];
        let permissionTypes = ['Ijin Klinik', 'Ijin Rumah Sakit'];
        let updateHistory = [];
        let notificationDays = 60;
        let deleteId = null;
        
        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            // Load data from localStorage
            loadDataFromStorage();
            
            // Initialize navigation
            initNavigation();
            
            // Initialize modals
            initModals();
            
            // Initialize forms
            initForms();
            
            // Initialize filters
            initFilters();
            
            // Initialize settings
            initSettings();
            
            // Initialize export
            initExport();
            
            // Render initial data
            renderDashboard();
            renderPermissionTypes();
            renderNotifications();
        });
        
        // Load data from localStorage
        function loadDataFromStorage() {
            const savedPermissions = localStorage.getItem('permissions');
            if (savedPermissions) {
                permissions = JSON.parse(savedPermissions);
            }
            
            const savedPermissionTypes = localStorage.getItem('permissionTypes');
            if (savedPermissionTypes) {
                permissionTypes = JSON.parse(savedPermissionTypes);
            }
            
            const savedUpdateHistory = localStorage.getItem('updateHistory');
            if (savedUpdateHistory) {
                updateHistory = JSON.parse(savedUpdateHistory);
            }
            
            const savedNotificationDays = localStorage.getItem('notificationDays');
            if (savedNotificationDays) {
                notificationDays = parseInt(savedNotificationDays);
                document.getElementById('notification-days').textContent = notificationDays;
                document.getElementById('notification-days-input').value = notificationDays;
            }
        }
        
        // Save data to localStorage
        function saveDataToStorage() {
            localStorage.setItem('permissions', JSON.stringify(permissions));
            localStorage.setItem('permissionTypes', JSON.stringify(permissionTypes));
            localStorage.setItem('updateHistory', JSON.stringify(updateHistory));
            localStorage.setItem('notificationDays', notificationDays.toString());
        }
        
        // Initialize navigation
        function initNavigation() {
            const navLinks = document.querySelectorAll('.nav-link');
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    // Remove active class from all links
                    navLinks.forEach(l => l.classList.remove('active'));
                    
                    // Add active class to clicked link
                    this.classList.add('active');
                    
                    // Hide all pages
                    document.querySelectorAll('.page-content').forEach(page => {
                        page.classList.remove('active');
                    });
                    
                    // Show selected page
                    const pageId = this.getAttribute('data-page') + '-page';
                    document.getElementById(pageId).classList.add('active');
                });
            });
        }
        
        // Initialize modals
        function initModals() {
            // Permission type change handler for add modal
            document.getElementById('permission-type').addEventListener('change', function() {
                const customTypeGroup = document.getElementById('custom-permission-type-group');
                if (this.value === 'Lainnya') {
                    customTypeGroup.style.display = 'block';
                    document.getElementById('custom-permission-type').setAttribute('required', 'required');
                } else {
                    customTypeGroup.style.display = 'none';
                    document.getElementById('custom-permission-type').removeAttribute('required');
                }
            });
            
            // Permission type change handler for edit modal
            document.getElementById('edit-permission-type').addEventListener('change', function() {
                const customTypeGroup = document.getElementById('edit-custom-permission-type-group');
                if (this.value === 'Lainnya') {
                    customTypeGroup.style.display = 'block';
                    document.getElementById('edit-custom-permission-type').setAttribute('required', 'required');
                } else {
                    customTypeGroup.style.display = 'none';
                    document.getElementById('edit-custom-permission-type').removeAttribute('required');
                }
            });
        }
        
        // Initialize forms
        function initForms() {
            // Add permission form
            document.getElementById('save-permission').addEventListener('click', function() {
                const form = document.getElementById('add-permission-form');
                if (form.checkValidity()) {
                    const type = document.getElementById('permission-type').value;
                    const customType = document.getElementById('custom-permission-type').value;
                    const finalType = type === 'Lainnya' ? customType : type;
                    const description = document.getElementById('permission-description').value;
                    const issueDate = document.getElementById('issue-date').value;
                    const expiryDate = document.getElementById('expiry-date').value;
                    
                    const newPermission = {
                        id: Date.now().toString(),
                        type: finalType,
                        description: description,
                        issueDate: issueDate,
                        expiryDate: expiryDate,
                        status: calculateStatus(expiryDate)
                    };
                    
                    permissions.push(newPermission);
                    saveDataToStorage();
                    
                    // Close modal
                    const modal = bootstrap.Modal.getInstance(document.getElementById('addPermissionModal'));
                    modal.hide();
                    
                    // Reset form
                    form.reset();
                    document.getElementById('custom-permission-type-group').style.display = 'none';
                    
                    // Show success message
                    showToast('Ijin berhasil ditambahkan', 'success');
                    
                    // Refresh data
                    renderDashboard();
                    renderNotifications();
                } else {
                    form.reportValidity();
                }
            });
            
            // Edit permission form
            document.getElementById('update-permission').addEventListener('click', function() {
                const form = document.getElementById('edit-permission-form');
                if (form.checkValidity()) {
                    const id = document.getElementById('edit-permission-id').value;
                    const type = document.getElementById('edit-permission-type').value;
                    const customType = document.getElementById('edit-custom-permission-type').value;
                    const finalType = type === 'Lainnya' ? customType : type;
                    const description = document.getElementById('edit-permission-description').value;
                    const issueDate = document.getElementById('edit-issue-date').value;
                    const expiryDate = document.getElementById('edit-expiry-date').value;
                    
                    const permissionIndex = permissions.findIndex(p => p.id === id);
                    if (permissionIndex !== -1) {
                        permissions[permissionIndex] = {
                            ...permissions[permissionIndex],
                            type: finalType,
                            description: description,
                            issueDate: issueDate,
                            expiryDate: expiryDate,
                            status: calculateStatus(expiryDate)
                        };
                        
                        saveDataToStorage();
                        
                        // Close modal
                        const modal = bootstrap.Modal.getInstance(document.getElementById('editPermissionModal'));
                        modal.hide();
                        
                        // Reset form
                        form.reset();
                        document.getElementById('edit-custom-permission-type-group').style.display = 'none';
                        
                        // Show success message
                        showToast('Ijin berhasil diperbarui', 'success');
                        
                        // Refresh data
                        renderDashboard();
                        renderNotifications();
                    }
                } else {
                    form.reportValidity();
                }
            });
            
            // Update permission form
            document.getElementById('save-update-permission').addEventListener('click', function() {
                const form = document.getElementById('update-permission-form');
                if (form.checkValidity()) {
                    const id = document.getElementById('update-permission-id').value;
                    const newExpiryDate = document.getElementById('update-expiry-date').value;
                    const note = document.getElementById('update-note').value;
                    
                    const permissionIndex = permissions.findIndex(p => p.id === id);
                    if (permissionIndex !== -1) {
                        const permission = permissions[permissionIndex];
                        
                        // Add to history
                        const historyEntry = {
                            id: Date.now().toString(),
                            permissionId: id,
                            type: permission.type,
                            description: permission.description,
                            updateDate: new Date().toISOString().split('T')[0],
                            newExpiryDate: newExpiryDate,
                            note: note
                        };
                        
                        updateHistory.push(historyEntry);
                        
                        // Update permission
                        permissions[permissionIndex] = {
                            ...permission,
                            expiryDate: newExpiryDate,
                            status: calculateStatus(newExpiryDate)
                        };
                        
                        saveDataToStorage();
                        
                        // Close modal
                        const modal = bootstrap.Modal.getInstance(document.getElementById('updatePermissionModal'));
                        modal.hide();
                        
                        // Reset form
                        form.reset();
                        
                        // Show success message
                        showToast('Ijin berhasil diperbarui', 'success');
                        
                        // Refresh data
                        renderDashboard();
                        renderNotifications();
                    }
                } else {
                    form.reportValidity();
                }
            });
            
            // Delete confirmation
            document.getElementById('confirm-delete').addEventListener('click', function() {
                if (deleteId) {
                    permissions = permissions.filter(p => p.id !== deleteId);
                    saveDataToStorage();
                    
                    // Close modal
                    const modal = bootstrap.Modal.getInstance(document.getElementById('deleteConfirmationModal'));
                    modal.hide();
                    
                    // Reset deleteId
                    deleteId = null;
                    
                    // Show success message
                    showToast('Ijin berhasil dihapus', 'success');
                    
                    // Refresh data
                    renderDashboard();
                    renderNotifications();
                }
            });
        }
        
        // Initialize filters
        function initFilters() {
            // Search input
            document.getElementById('search-input').addEventListener('input', function() {
                filterPermissions();
            });
            
            // Filter category
            document.getElementById('filter-category').addEventListener('change', function() {
                filterPermissions();
            });
            
            // Filter status
            document.getElementById('filter-status').addEventListener('change', function() {
                filterPermissions();
            });
            
            // Sort by
            document.getElementById('sort-by').addEventListener('change', function() {
                sortPermissions();
            });
            
            // Reset filter
            document.getElementById('reset-filter').addEventListener('click', function() {
                document.getElementById('search-input').value = '';
                document.getElementById('filter-category').value = '';
                document.getElementById('filter-status').value = '';
                document.getElementById('sort-by').value = '';
                
                renderPermissions();
            });
        }
        
        // Initialize settings
        function initSettings() {
            // Add permission type
            document.getElementById('add-permission-type').addEventListener('click', function() {
                const newType = document.getElementById('new-permission-type').value.trim();
                if (newType) {
                    if (!permissionTypes.includes(newType)) {
                        permissionTypes.push(newType);
                        saveDataToStorage();
                        
                        // Update dropdowns
                        updatePermissionTypeDropdowns();
                        
                        // Reset input
                        document.getElementById('new-permission-type').value = '';
                        
                        // Refresh data
                        renderPermissionTypes();
                        
                        // Show success message
                        showToast('Jenis ijin berhasil ditambahkan', 'success');
                    } else {
                        showToast('Jenis ijin sudah ada', 'warning');
                    }
                }
            });
            
            // Save notification settings
            document.getElementById('save-notification-settings').addEventListener('click', function() {
                const days = parseInt(document.getElementById('notification-days-input').value);
                if (days > 0 && days <= 365) {
                    notificationDays = days;
                    saveDataToStorage();
                    
                    // Update notification display
                    document.getElementById('notification-days').textContent = notificationDays;
                    
                    // Refresh notifications
                    renderNotifications();
                    
                    // Show success message
                    showToast('Pengaturan notifikasi berhasil disimpan', 'success');
                } else {
                    showToast('Harap masukkan angka antara 1 dan 365', 'warning');
                }
            });
        }
        
        // Initialize export
        function initExport() {
            document.getElementById('export-btn').addEventListener('click', function() {
                exportToExcel();
            });
        }
        
        // Calculate permission status
        function calculateStatus(expiryDate) {
            const today = new Date();
            const expiry = new Date(expiryDate);
            const diffTime = expiry - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            
            if (diffDays < 0) {
                return 'Kadaluarsa';
            } else if (diffDays <= notificationDays) {
                return 'Akan Kadaluarsa';
            } else {
                return 'Aktif';
            }
        }
        
        // Render dashboard
        function renderDashboard() {
            // Calculate statistics
            const totalPermissions = permissions.length;
            const activePermissions = permissions.filter(p => p.status === 'Aktif').length;
            const expiringPermissions = permissions.filter(p => p.status === 'Akan Kadaluarsa').length;
            const expiredPermissions = permissions.filter(p => p.status === 'Kadaluarsa').length;
            
            // Update statistics
            document.getElementById('total-permissions').textContent = totalPermissions;
            document.getElementById('active-permissions').textContent = activePermissions;
            document.getElementById('expiring-permissions').textContent = expiringPermissions;
            document.getElementById('expired-permissions').textContent = expiredPermissions;
            
            // Render permissions table
            renderPermissions();
        }
        
        // Render permissions
        function renderPermissions() {
            const tbody = document.getElementById('permissions-tbody');
            tbody.innerHTML = '';
            
            if (permissions.length === 0) {
                tbody.innerHTML = '<tr><td colspan="7" class="text-center">Belum ada data perijinan</td></tr>';
            } else {
                permissions.forEach((permission, index) => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${index + 1}</td>
                        <td>${permission.type}</td>
                        <td>${permission.description}</td>
                        <td>${formatDate(permission.issueDate)}</td>
                        <td>${formatDate(permission.expiryDate)}</td>
                        <td><span class="status-badge status-${permission.status === 'Aktif' ? 'active' : permission.status === 'Kadaluarsa' ? 'expired' : 'warning'}">${permission.status}</span></td>
                        <td>
                            <div class="action-buttons">
                                <button class="btn btn-sm btn-outline-primary edit-btn" data-id="${permission.id}" title="Edit">
                                    <i class="bi bi-pencil me-1"></i> Edit
                                </button>
                                <button class="btn btn-sm btn-outline-success update-btn" data-id="${permission.id}" title="Perbarui">
                                    <i class="bi bi-arrow-clockwise me-1"></i> Perbarui
                                </button>
                                <button class="btn btn-sm btn-outline-info history-btn" data-id="${permission.id}" title="Riwayat">
                                    <i class="bi bi-clock-history me-1"></i> Riwayat
                                </button>
                                <button class="btn btn-sm btn-outline-danger delete-btn" data-id="${permission.id}" title="Hapus">
                                    <i class="bi bi-trash me-1"></i> Hapus
                                </button>
                            </div>
                        </td>
                    `;
                    tbody.appendChild(row);
                });
                
                // Add event listeners to action buttons
                document.querySelectorAll('#permissions-tbody .edit-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openEditModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .update-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openUpdateModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .history-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openHistoryModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .delete-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openDeleteModal(this.getAttribute('data-id'));
                    });
                });
            }
        }
        
        // Render permission types
        function renderPermissionTypes() {
            const tbody = document.getElementById('permission-types-tbody');
            tbody.innerHTML = '';
            
            if (permissionTypes.length === 0) {
                tbody.innerHTML = '<tr><td colspan="3" class="text-center">Belum ada jenis ijin</td></tr>';
            } else {
                permissionTypes.forEach((type, index) => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${index + 1}</td>
                        <td>${type}</td>
                        <td>
                            <button class="btn btn-sm btn-outline-danger delete-type-btn" data-type="${type}" title="Hapus">
                                <i class="bi bi-trash me-1"></i> Hapus
                            </button>
                        </td>
                    `;
                    tbody.appendChild(row);
                });
                
                // Add event listeners to delete buttons
                document.querySelectorAll('#permission-types-tbody .delete-type-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const type = this.getAttribute('data-type');
                        if (confirm(`Apakah Anda yakin ingin menghapus jenis ijin "${type}"?`)) {
                            permissionTypes = permissionTypes.filter(t => t !== type);
                            saveDataToStorage();
                            
                            // Update dropdowns
                            updatePermissionTypeDropdowns();
                            
                            // Refresh data
                            renderPermissionTypes();
                            
                            // Show success message
                            showToast('Jenis ijin berhasil dihapus', 'success');
                        }
                    });
                });
            }
        }
        
        // Render notifications
        function renderNotifications() {
            const today = new Date();
            const notificationDate = new Date(today);
            notificationDate.setDate(today.getDate() + notificationDays);
            
            // Find permissions that will expire within the notification period
            const expiringPermissions = permissions.filter(p => {
                const expiryDate = new Date(p.expiryDate);
                return expiryDate <= notificationDate && expiryDate >= today;
            });
            
            const notificationList = document.getElementById('expiring-permissions-list');
            const notificationCount = document.getElementById('notification-count');
            
            notificationCount.textContent = expiringPermissions.length;
            
            if (expiringPermissions.length === 0) {
                notificationList.innerHTML = `<p class="text-muted">Tidak ada ijin yang akan kadaluarsa dalam ${notificationDays} hari ke depan.</p>`;
            } else {
                notificationList.innerHTML = '';
                
                // Sort by expiry date (soonest first)
                expiringPermissions.sort((a, b) => new Date(a.expiryDate) - new Date(b.expiryDate));
                
                expiringPermissions.forEach(permission => {
                    const expiryDate = new Date(permission.expiryDate);
                    const diffTime = expiryDate - today;
                    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                    
                    const expiringCard = document.createElement('div');
                    expiringCard.className = 'expiring-card';
                    expiringCard.innerHTML = `
                        <div class="card-body">
                            <div class="d-flex justify-content-between align-items-center">
                                <div>
                                    <h6 class="mb-1">${permission.description}</h6>
                                    <p class="mb-0 text-muted">${permission.type}</p>
                                </div>
                                <div class="text-end">
                                    <div class="days-left">${diffDays} hari lagi</div>
                                    <div class="small text-muted">${formatDate(permission.expiryDate)}</div>
                                </div>
                            </div>
                            <div class="mt-2">
                                <button class="btn btn-sm btn-primary update-btn" data-id="${permission.id}">Perbarui Sekarang</button>
                            </div>
                        </div>
                    `;
                    notificationList.appendChild(expiringCard);
                });
                
                // Add event listeners to update buttons
                document.querySelectorAll('#expiring-permissions-list .update-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openUpdateModal(this.getAttribute('data-id'));
                    });
                });
            }
        }
        
        // Filter permissions
        function filterPermissions() {
            const searchTerm = document.getElementById('search-input').value.toLowerCase();
            const categoryFilter = document.getElementById('filter-category').value;
            const statusFilter = document.getElementById('filter-status').value;
            
            let filteredPermissions = permissions.filter(permission => {
                const matchesSearch = permission.description.toLowerCase().includes(searchTerm) || 
                                     permission.type.toLowerCase().includes(searchTerm);
                const matchesCategory = !categoryFilter || permission.type === categoryFilter;
                const matchesStatus = !statusFilter || permission.status === statusFilter;
                
                return matchesSearch && matchesCategory && matchesStatus;
            });
            
            // Update table with filtered results
            const tbody = document.getElementById('permissions-tbody');
            tbody.innerHTML = '';
            
            if (filteredPermissions.length === 0) {
                tbody.innerHTML = '<tr><td colspan="7" class="text-center">Tidak ada data perijinan yang sesuai dengan filter</td></tr>';
            } else {
                filteredPermissions.forEach((permission, index) => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${index + 1}</td>
                        <td>${permission.type}</td>
                        <td>${permission.description}</td>
                        <td>${formatDate(permission.issueDate)}</td>
                        <td>${formatDate(permission.expiryDate)}</td>
                        <td><span class="status-badge status-${permission.status === 'Aktif' ? 'active' : permission.status === 'Kadaluarsa' ? 'expired' : 'warning'}">${permission.status}</span></td>
                        <td>
                            <div class="action-buttons">
                                <button class="btn btn-sm btn-outline-primary edit-btn" data-id="${permission.id}" title="Edit">
                                    <i class="bi bi-pencil me-1"></i> Edit
                                </button>
                                <button class="btn btn-sm btn-outline-success update-btn" data-id="${permission.id}" title="Perbarui">
                                    <i class="bi bi-arrow-clockwise me-1"></i> Perbarui
                                </button>
                                <button class="btn btn-sm btn-outline-info history-btn" data-id="${permission.id}" title="Riwayat">
                                    <i class="bi bi-clock-history me-1"></i> Riwayat
                                </button>
                                <button class="btn btn-sm btn-outline-danger delete-btn" data-id="${permission.id}" title="Hapus">
                                    <i class="bi bi-trash me-1"></i> Hapus
                                </button>
                            </div>
                        </td>
                    `;
                    tbody.appendChild(row);
                });
                
                // Add event listeners to action buttons
                document.querySelectorAll('#permissions-tbody .edit-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openEditModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .update-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openUpdateModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .history-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openHistoryModal(this.getAttribute('data-id'));
                    });
                });
                
                document.querySelectorAll('#permissions-tbody .delete-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        openDeleteModal(this.getAttribute('data-id'));
                    });
                });
            }
        }
        
        // Sort permissions
        function sortPermissions() {
            const sortBy = document.getElementById('sort-by').value;
            
            if (!sortBy) {
                renderPermissions();
                return;
            }
            
            let sortedPermissions = [...permissions];
            
            switch (sortBy) {
                case 'category':
                    sortedPermissions.sort((a, b) => a.type.localeCompare(b.type));
                    break;
                case 'endDate':
                    sortedPermissions.sort((a, b) => new Date(a.expiryDate) - new Date(b.expiryDate));
                    break;
                case 'status':
                    sortedPermissions.sort((a, b) => a.status.localeCompare(b.status));
                    break;
            }
            
            // Update table with sorted results
            const tbody = document.getElementById('permissions-tbody');
            tbody.innerHTML = '';
            
            sortedPermissions.forEach((permission, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${permission.type}</td>
                    <td>${permission.description}</td>
                    <td>${formatDate(permission.issueDate)}</td>
                    <td>${formatDate(permission.expiryDate)}</td>
                    <td><span class="status-badge status-${permission.status === 'Aktif' ? 'active' : permission.status === 'Kadaluarsa' ? 'expired' : 'warning'}">${permission.status}</span></td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn btn-sm btn-outline-primary edit-btn" data-id="${permission.id}" title="Edit">
                                <i class="bi bi-pencil me-1"></i> Edit
                            </button>
                            <button class="btn btn-sm btn-outline-success update-btn" data-id="${permission.id}" title="Perbarui">
                                <i class="bi bi-arrow-clockwise me-1"></i> Perbarui
                            </button>
                            <button class="btn btn-sm btn-outline-info history-btn" data-id="${permission.id}" title="Riwayat">
                                <i class="bi bi-clock-history me-1"></i> Riwayat
                            </button>
                            <button class="btn btn-sm btn-outline-danger delete-btn" data-id="${permission.id}" title="Hapus">
                                <i class="bi bi-trash me-1"></i> Hapus
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            // Add event listeners to action buttons
            document.querySelectorAll('#permissions-tbody .edit-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    openEditModal(this.getAttribute('data-id'));
                });
            });
            
            document.querySelectorAll('#permissions-tbody .update-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    openUpdateModal(this.getAttribute('data-id'));
                });
            });
            
            document.querySelectorAll('#permissions-tbody .history-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    openHistoryModal(this.getAttribute('data-id'));
                });
            });
            
            document.querySelectorAll('#permissions-tbody .delete-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    openDeleteModal(this.getAttribute('data-id'));
                });
            });
        }
        
        // Open edit modal
        function openEditModal(id) {
            const permission = permissions.find(p => p.id === id);
            if (permission) {
                document.getElementById('edit-permission-id').value = permission.id;
                
                // Set permission type
                const isCustomType = !permissionTypes.includes(permission.type);
                if (isCustomType) {
                    document.getElementById('edit-permission-type').value = 'Lainnya';
                    document.getElementById('edit-custom-permission-type').value = permission.type;
                    document.getElementById('edit-custom-permission-type-group').style.display = 'block';
                    document.getElementById('edit-custom-permission-type').setAttribute('required', 'required');
                } else {
                    document.getElementById('edit-permission-type').value = permission.type;
                    document.getElementById('edit-custom-permission-type-group').style.display = 'none';
                    document.getElementById('edit-custom-permission-type').removeAttribute('required');
                }
                
                document.getElementById('edit-permission-description').value = permission.description;
                document.getElementById('edit-issue-date').value = permission.issueDate;
                document.getElementById('edit-expiry-date').value = permission.expiryDate;
                
                // Open modal
                const modal = new bootstrap.Modal(document.getElementById('editPermissionModal'));
                modal.show();
            }
        }
        
        // Open update modal
        function openUpdateModal(id) {
            const permission = permissions.find(p => p.id === id);
            if (permission) {
                document.getElementById('update-permission-id').value = permission.id;
                document.getElementById('update-expiry-date').value = permission.expiryDate;
                document.getElementById('update-note').value = '';
                
                // Open modal
                const modal = new bootstrap.Modal(document.getElementById('updatePermissionModal'));
                modal.show();
            }
        }
        
        // Open history modal
        function openHistoryModal(id) {
            const permission = permissions.find(p => p.id === id);
            if (permission) {
                // Find history entries for this permission
                const permissionHistory = updateHistory.filter(h => h.permissionId === id);
                
                // Update modal title
                document.getElementById('permissionHistoryModalLabel').textContent = `Riwayat Perijinan - ${permission.description}`;
                
                // Render history table
                const tbody = document.getElementById('permission-history-tbody');
                tbody.innerHTML = '';
                
                if (permissionHistory.length === 0) {
                    tbody.innerHTML = '<tr><td colspan="3" class="text-center">Belum ada riwayat perbaruan untuk ijin ini</td></tr>';
                } else {
                    // Sort by date (newest first)
                    const sortedHistory = [...permissionHistory].sort((a, b) => new Date(b.updateDate) - new Date(a.updateDate));
                    
                    sortedHistory.forEach(entry => {
                        const row = document.createElement('tr');
                        row.innerHTML = `
                            <td>${formatDate(entry.updateDate)}</td>
                            <td>${formatDate(entry.newExpiryDate)}</td>
                            <td>${entry.note || '-'}</td>
                        `;
                        tbody.appendChild(row);
                    });
                }
                
                // Open modal
                const modal = new bootstrap.Modal(document.getElementById('permissionHistoryModal'));
                modal.show();
            }
        }
        
        // Open delete modal
        function openDeleteModal(id) {
            deleteId = id;
            const modal = new bootstrap.Modal(document.getElementById('deleteConfirmationModal'));
            modal.show();
        }
        
        // Update permission type dropdowns
        function updatePermissionTypeDropdowns() {
            // Update add modal dropdown
            const addDropdown = document.getElementById('permission-type');
            const currentAddValue = addDropdown.value;
            addDropdown.innerHTML = '<option value="" selected disabled>Pilih jenis ijin</option>';
            
            permissionTypes.forEach(type => {
                const option = document.createElement('option');
                option.value = type;
                option.textContent = type;
                addDropdown.appendChild(option);
            });
            
            const otherOption = document.createElement('option');
            otherOption.value = 'Lainnya';
            otherOption.textContent = 'Lainnya';
            addDropdown.appendChild(otherOption);
            
            if (currentAddValue) {
                addDropdown.value = currentAddValue;
            }
            
            // Update edit modal dropdown
            const editDropdown = document.getElementById('edit-permission-type');
            const currentEditValue = editDropdown.value;
            editDropdown.innerHTML = '<option value="" selected disabled>Pilih jenis ijin</option>';
            
            permissionTypes.forEach(type => {
                const option = document.createElement('option');
                option.value = type;
                option.textContent = type;
                editDropdown.appendChild(option);
            });
            
            const editOtherOption = document.createElement('option');
            editOtherOption.value = 'Lainnya';
            editOtherOption.textContent = 'Lainnya';
            editDropdown.appendChild(editOtherOption);
            
            if (currentEditValue) {
                editDropdown.value = currentEditValue;
            }
            
            // Update filter dropdown
            const filterDropdown = document.getElementById('filter-category');
            const currentFilterValue = filterDropdown.value;
            filterDropdown.innerHTML = '<option value="">Semua Kategori</option>';
            
            permissionTypes.forEach(type => {
                const option = document.createElement('option');
                option.value = type;
                option.textContent = type;
                filterDropdown.appendChild(option);
            });
            
            const filterOtherOption = document.createElement('option');
            filterOtherOption.value = 'Lainnya';
            filterOtherOption.textContent = 'Lainnya';
            filterDropdown.appendChild(filterOtherOption);
            
            if (currentFilterValue) {
                filterDropdown.value = currentFilterValue;
            }
        }
        
        // Export to Excel
        function exportToExcel() {
            // Create a new workbook
            const wb = XLSX.utils.book_new();
            
            // Convert permissions data to worksheet
            const wsData = permissions.map(p => ({
                'Jenis Ijin': p.type,
                'Deskripsi': p.description,
                'Tanggal Terbit': formatDate(p.issueDate),
                'Tanggal Akhir': formatDate(p.expiryDate),
                'Status': p.status
            }));
            
            const ws = XLSX.utils.json_to_sheet(wsData);
            
            // Add worksheet to workbook
            XLSX.utils.book_append_sheet(wb, ws, 'Data Perijinan');
            
            // Generate filename with current date
            const today = new Date();
            const filename = `Data_Perijinan_${formatDate(today.toISOString().split('T')[0])}.xlsx`;
            
            // Save the file
            XLSX.writeFile(wb, filename);
            
            // Show success message
            showToast('Data berhasil diekspor ke Excel', 'success');
        }
        
        // Format date
        function formatDate(dateString) {
            const date = new Date(dateString);
            const day = date.getDate().toString().padStart(2, '0');
            const month = (date.getMonth() + 1).toString().padStart(2, '0');
            const year = date.getFullYear();
            
            return `${day}/${month}/${year}`;
        }
        
        // Show toast notification
        function showToast(message, type = 'info') {
            const toastContainer = document.querySelector('.toast-container');
            
            const toastId = 'toast-' + Date.now();
            const toastHtml = `
                <div id="${toastId}" class="toast custom-toast align-items-center text-white bg-${type === 'success' ? 'success' : type === 'warning' ? 'warning' : type === 'danger' ? 'danger' : 'primary'} border-0" role="alert" aria-live="assertive" aria-atomic="true">
                    <div class="d-flex">
                        <div class="toast-body">
                            ${message}
                        </div>
                        <button type="button" class="btn-close btn-close-white me-2 m-auto" data-bs-dismiss="toast" aria-label="Close"></button>
                    </div>
                </div>
            `;
            
            toastContainer.insertAdjacentHTML('beforeend', toastHtml);
            
            const toastElement = document.getElementById(toastId);
            const toast = new bootstrap.Toast(toastElement, {
                autohide: true,
                delay: 3000
            });
            
            toast.show();
            
            // Remove toast element after hidden
            toastElement.addEventListener('hidden.bs.toast', function() {
                toastElement.remove();
            });
        }
    </script>
</body>
</html>
